---
title: (Accidentally) fishing for crypto wallet scam sites 💸
description: 
date: 2022-08-17
tags: [phishing, security]
draft: false
---

A friend recently asked for suggestions on safe storage options for their cryptocurrency (spoiler: the safe place is not on the exchange where you bought it). I wanted to suggest some hardware wallets, but I couldn't remember the exact URLs for the Trezor and Ledger sites, so I pulled up DuckDuckGo and searched for “trezor wallet.”

Wary of malicious SEO and fraudulent ads, I skimmed the first few results and immediately noticed something odd: `trezorwalle.com` was the second search result. I pulled up the site in a sandboxed window and opened the real Trezor site, `trezor.io`, for reference. `trezorwalle.com` is a clone of `trezor.io`, and when I initially examined it, all the links on the cloned page pointed back to `trezor.io`.

{{< figure src ="/images/crypto-wallets/trezorwalle_ddg.png" >}} 

_DuckDuckGo search results for "trezor wallet."_


This was around dinnertime, so I stepped away to eat and unwind a bit, but afterwards I was still thinking about the cloned Trezor site. I came back to it about an hour later and noticed that the links in the top navigation menu had changed, all pointing to `https://surphyeaskets.com/ed473857-c0f7-4564-baff-ef491bec5210`. This URL redirected to `suite.trezor.io`.

{{< figure src ="/images/crypto-wallets/real_fake_trezor_screenshots.png" >}} 
_Can you spot the real Trezor site?_

Well, now I had to dig in a little more. Settling in at my laptop, I began with a quick whois and dig on `trezorwalle.com`, which yielded the following results:

```
whois trezorwalle.com
   Domain Name: TREZORWALLE.COM
   Registry Domain ID: 2703986123_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.eranet.com
   Registrar URL: http://www.eranet.com
   Updated Date: 2022-06-16T11:45:18Z
   Creation Date: 2022-06-15T10:48:33Z
(truncated for readability)

dig +short trezorwalle.com
185.244.36.154
```

In case there were any doubts, it's clear this site isn't associated with the real Trezor wallet company. [Censys shows](https://censys.io/login?came_from=https%3A%2F%2Fsearch.censys.io%2Fhosts%2F185.244.36.154%3Fat_time%3D2022-08-17T03%253A38%253A59.355Z&from_censys_owned_external=True) a number of HTTP services active on this host at the time, which could point to the host being used to serve multiple (fraudulent) sites at different times.

I fired up Burp Suite’s Proxy to see if there might be interesting requests being made as the fraudulent site loaded, and who would’ve guessed–the site reaches out to a strikingly similar (and equally fraudulent) domain, `trezorwallett.com`. These requests all 404’d:

{{< figure src ="/images/crypto-wallets/burp_traffic_wallett.png" >}}

_Burp Suite’s Proxy interface showing failed GET requests to `trezorwallett.com`._

Registered via the same registrar, though on different dates, this site appears to be fronted by two [Cloudflare](https://search.censys.io/hosts/172.67.144.100) [load balancers](https://search.censys.io/hosts/104.21.71.104). The domain resolved at the time of investigation, though:


{{< figure src ="/images/crypto-wallets/trezorwallett_homepage_bigger.png" >}}

_Whoops._

# The Medium Connection
I continued my investigation by searching Google for “trezorwalle.com". Apart from a "business profile" for "Trezor", I noticed a Medium site that contains what appear to be possible SEO attempts for several crypto-related typosquatting / phishing sites. There was also a Pinterest profile with similar content, though it was less detailed, and focused solely on `trezorwalle.com`.


{{< figure src ="/images/crypto-wallets/trezorwalle.com_google.png" >}}

_Google results with Medium site containing text about `trezorwalle.com`._


{{< figure src ="/images/crypto-wallets/pinterest_trezorwalle.com.png" >}} 

_Pinterest profile linking `trezorwalle.com` with more seemingly legitimate Trezor text._

{{< figure src ="/images/crypto-wallets/medium_site_trezorwalle_snippet.png" >}} 

_Medium post about the merits of Trezor wallet, with link to `trezorwalle.com`._

These Medium posts combine legitimate text about the real service being impersonated with a link to the fraudulent domain. When cautious users search for the domains–perhaps trying to vet a URL they've received in an email–reassuring text will appear alongside the fraudulent domain, likely in an attempt to lend legitimacy to the phishing site. Examples of additional Medium posts:

{{< figure src ="/images/crypto-wallets/medium_binance.png" >}}

{{< figure src ="/images/crypto-wallets/medium_how_buy_btc.png" >}}

{{< figure src ="/images/crypto-wallets/medium_mmask.png" >}}

{{< figure src ="/images/crypto-wallets/medium_uphold.png" >}}

When examining some of the domains from the URLs in the screenshots above, we see that they are also registered via the same registrar, EraNet, over a period of time beginning in late 2021. The earliest registered domain from those examined appears to be `cryptowalletts.com`, registered in September 2021.

```
whois coinbaswallet.com
   Domain Name: COINBASWALLET.COM
   Registry Domain ID: 2707322144_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.eranet.com
   Registrar URL: http://www.eranet.com
   Updated Date: 2022-06-29T08:22:56Z
   Creation Date: 2022-06-29T05:55:03Z

whois cryptowalletts.com
   Domain Name: CRYPTOWALLETTS.COM
   Registry Domain ID: 2639049150_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.eranet.com
   Registrar URL: http://www.eranet.com
   Updated Date: 2022-04-22T16:08:03Z
   Creation Date: 2021-09-06T11:52:02Z
   ```

# The Intermediary Domain and Github Repos
Returning to the domain linked in the fraudulent Trezor site, I began searching for `surphyeaskets.com` and found the following Github users and repos. Each are misspellings of popular crypto wallets and were created between 9 and 11 days ago as of this writing:

{{< figure src ="/images/crypto-wallets/surphyeaskets_pivot_ddg_results.png" >}}

_DuckDuckGo search for the domain name found on `trezorwalle.com`._

Each of these repos contain a nearly identical `index.html` file with an image of the wallet being spoofed and a link that points to `surphyeaskets.com` followed by a unique alphanumeric string. The users are no longer active as of this writing and attempting to access their profiles results in a 404. 

{{< figure src ="/images/crypto-wallets/krakenlogi_index_html.png" >}}

_Repo for user `krakenlogi` showing `index.html` with link to `surphyeaskets.com` the body._


# Closing Thoughts
It’s been a bit since I dug into phishing pages, but the apparent SEO on Medium and other sites is an interesting tactic. It’s a great example of how misinformation can be planted and spread when the SEO is effective–almost like a form of astroturfing.

`trezorwalle.com` and the three Github repos associated with Kraken, Phantom, and MetaMask impersonations no longer appear to be active as of the evening of August 17, 2022. However, the spread of registration dates for the domains associated with this potential campaign–going all the way back to September 2021–suggests that whoever’s behind it will likely be at it again soon. 

Crypto investors, keep your eyes open. Double- and triple-check emails you receive from any exchanges, wallet companies, or other organizations purporting to be related to any cryptocurrency dealings. 👀

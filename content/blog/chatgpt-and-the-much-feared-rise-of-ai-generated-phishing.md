---
title: ChatGPT and the much-feared rise of AI-generated phishing 🤖
description: 
date: 2023-01-06
tags: [ai, phishing, musings, security]
---

If you've been online, well, at all lately you've probably seen screenshots of "conversations" with OpenAI's ChatGPT plastered all over social media. If not, here's one for your reading pleasure:

{{< figure src="/images/chat-gpt/marathon-chatgpt.png" title="ChatGPT's idea of a marathon training plan. This feels like a scrape of the top posts mentioning 'marathon training' from r/running standing on top of one another in a trenchcoat." >}}

If you follow security or AI ethics news, you've also probably already seen much [musing](https://abnormalsecurity.com/blog/double-edged-sword-of-chatgpt) and [concern](https://www.axios.com/2023/01/03/hackers-chatgpt-cybercrime-help) around threat actors adopting ChatGPT to craft more effective malicious emails. This is undoubtedly already happening. I don't have concrete evidence of it, but knowing that threat actors adopt [new tools](https://news.yahoo.com/college-student-created-app-detect-170700002.html) just as legitimate operations do, it's highly likely they're already exploiting this new technology. While some tools now exist to determine whether text is organic or AI-generated, it may be some time before they’re refined enough to be incorporated into secure email products that detect and block malicious email. 

{{< figure src="/images/chat-gpt/phishing-chatgpt.png" title="ChatGPT wrote a nice phishing email for me and even indicated where I should include a link to the 'fake password reset page.'" >}}

While it's worth taking note of this new tool and how it might be abused, I don't think ChatGPT is going to lead to a catastrophic uptick in irresistibly clickable phishing links anytime soon.

Effective email filters and security products rely on multiple indicators to help classify a given message as [spam or ham](https://cwiki.apache.org/confluence/display/spamassassin/Ham). Metadata found in email headers, like the address of the host where the message originated, the actual sender's address, and DKIM, SPF, and DMARC checks are valuable tools in helping determine whether a message is malicious.

The body of the email is but one factor in detecting malicious email, and threat actors already have ways of circumventing checks against email bodies. Sometimes they'll base64 or URL encode the raw email or parts of it to make it more difficult for string matching rules to catch known-bad URLs or text. Even if threat actors use ChatGPT to craft their emails and SMS messages, they're likely still using similar infrastructure and other tools that can provide clues to a message's validity. 

Just as you (hopefully) wouldn’t rely solely on a single password for privileged network access, detecting AI-generated malicious messages shouldn’t hinge solely on how “convincing” the text is. It's important to carefully consider security and safety implications of emerging technology like ChatGPT, but it's equally important to think critically about these new problems as we grow and shape our defenses. 
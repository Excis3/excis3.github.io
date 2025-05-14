---
title: "Shitty reports, what NOT to report"
date: 2025-05-14 01:00:00 +0200
categories:
  Tutorials
  Practical
tags:
  how-to
  bugbounty
pin: true
mermaid: true
image:
  path: /Excis3/excis3.github.io/main/media/shitty_reports.jpg
---

When you look at the researcher counts on the four major bug bounty platforms, you’ll notice they all have **hundreds of thousands** of users. Impressive, right? But dig a little deeper, and you’ll see that only a **few thousand** of them are actually consistently submitting quality reports.
For example, my profiles rank somewhere between #1500 and #2000, and I haven’t even submitted that many vulnerabilities. So what’s going on?
The truth is, these platforms are flooded with **low-effort, low-quality reports**, the kind that get rejected instantly. Triagers have to deal with this noise every single day.
This blog post is about those reports: the ones you should never submit. If you’re serious about bug bounty hunting and want to build both your skills and your reputation, avoid these at all costs.


In this blog post:
1. **What not to report**
2. **What are valid reports**
3. **What to avoid when writing a report**


## What not to report

![logo-ccb.svg](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/bad_report.jpg)

Below are some examples of reports and explanations of why they should not be submitted. These are the kinds of reports that get rejected, usually because they’re incomplete, show no real impact, or, frankly, just don’t make any sense.

[Report Title]
> report or writing








## What are valid reports

![report.jpg](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/good_report.jpg)

A valid bug bounty report clearly demonstrates **real-world impact**, what an attacker could do to compromise a company or its users. As the researcher, your job is to provide a working proof of concept (PoC) where you act as the attacker (without causing disruption or modifying any real data) and show what’s actually possible.
Theoretical issues, where you merely suggest something might be exploitable, are almost never accepted. When you step into the attacker's shoes and back your report with a solid, reproducible PoC, your chances of having it accepted go way up.

However, there are a few important things to keep in mind:
- Always read the scope. Make sure the domain you're testing or the vulnerability type you're reporting isn't explicitly out of scope.
- Keep your attack scenario realistic. Ask yourself: Would I, as a company, pay for this issue? If the answer is no, it might be too complex, contrived, or low-impact.

For new researchers, I highly recommend learning the core vulnerabilities through PortSwigger Web Security Academy (portswigger.net/web-security). It's a free, hands-on platform with realistic labs that simulate exactly the kinds of bugs companies are paying for.
As a beginner, start with vulnerabilities where impact is easy to demonstrate, like XSS (Cross-Site Scripting) or IDOR (Insecure Direct Object Reference). These are great for learning how to show real consequences in a clear, actionable way.

On the other hand, avoid low-value reports like Clickjacking, CORS misconfigurations, or Response manipulation, especially early on. These are often misunderstood, hard to prove useful, and frequently rejected.

Bug bounty is part skill, part creativity, and part empathy, the kind where you ask: If I were a company, would I care? If the answer is yes, you’re on the right track. If the answer is “well, maybe if they’re really paranoid and bored,” you might want to dig deeper.



### What to avoid when writing a report

![report.jpg](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/maybe_report.jpg)

When you're writing a bug bounty report, there are certain words and phrases you should avoid. Using them often signals to the triager that you haven’t proven real impact, and your report is likely headed for rejection.
The most important part of your report is the title — it’s the first thing the triager or company sees. If your title says things like:
    “Potential RCE”
    “Possible issue”
    “Maybe vulnerable to X”

...you’re already halfway to getting rejected.
Here are some common examples, and how to avoid falling into these traps:

- “I found a possible RCE in XYZ, but I only got this error message.”
> What to do instead:
If you think you’ve found Remote Code Execution, prove it. Set up a PoC that triggers an outbound DNS or HTTP request to your Burp Collaborator or other interaction server. Without real evidence of code execution, the report won’t go far.

- “An attacker can do possible template injection.”
> What to do instead:
Don't stop at {{7*7}}. That just shows basic injection. Go further, can you read environment variables? Leak secrets? Execute logic? Show something an attacker would actually exploit. Prove impact.

- “I maybe found something…”
> What to do instead:
Vague statements like this scream “I didn’t finish my homework.” Don’t report every error message or weird behavior. Dig deeper. Think like an attacker: What can I do with this? Can I gain access, leak data, or escalate privileges?

Always ask yourself:
    “If I were a company, would I pay for this? Have I shown what an attacker can actually do?”

Then, back it up with a clear, working proof of concept.

Remember: Triagers aren't out to get you, but they are busy. Make their job easier by showing clear, direct impact. Avoid filler words and uncertain language. Be confident because your research backs it up.

Final Tip: Use AI Wisely:

Try to avoid submitting fully AI-generated reports, they often contain errors, misunderstand the context, or sound overly generic. However, AI can be a great tool to improve your writing, especially if English isn’t your first language.

Here’s a good workflow:
    - Write your report in your native language first, then translate it to English.
    - Or write it in English and use AI to refine the grammar, clarity, and structure.

Just be careful: never include sensitive, private, or company-specific information in any chatbot or translation tool. Always review and sanitize your content before sharing it with any external service.


## Conclusion

I hope this post helps clarify what should and shouldn’t be reported in bug bounty programs, especially for newer researchers. Submitting well-researched, impactful reports doesn’t just increase your own chances of success, it also improves the experience for triagers, programs, and the entire bug bounty community.
Triagers already have their hands full. Every low-quality or invalid report wastes time that could’ve been spent reviewing real, valuable findings. Let’s respect their time and raise the bar together.

Thanks for reading — and happy hacking!

**Excis3**

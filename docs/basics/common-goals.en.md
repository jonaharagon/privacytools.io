---
title: "Common Goals"
icon: 'material/eye-outline'
---

Broadly speaking, we categorize our recommendations into these general categories of threats or goals that apply to most people. ==You may be concerned with one, a few, or all of these possibilities==, and the tools and services you use depends on what your goals are. You may also have specific threats outside of these categories as well, which is perfectly fine! The important part is developing an understanding of the benefits and shortfallings of the tools you choose to use, because virtually none of them will protect you from every threat imaginable.

- <span class="pg-purple" title="Protects your activities from being tied to your real-life identity">:material-incognito: Anonymity</span> - Shielding your online activity from your real-life identity, protecting you from people who are trying to uncover your identity specifically.
- <span class="pg-red" title="Protects you from malicious agents targeting you specifically">:material-target-account: Targeted Attacks</span> - Being protected  from dedicated hackers or other malicious agents trying to gain access to *your* data or devices specifically.
- <span class="pg-orange" title="Protects you from malware and other passive attacks">:material-bug-outline: Passive Attacks</span> - Being protected from things like malware, data breaches, and other attacks that are made against many people at once.
- <span class="pg-teal" title="Protects your data from being readable by your service provider">:material-server-network: Service Providers</span> - Protecting your data from service providers, e.g. with end-to-end encryption rendering your data unreadable to the server.
- <span class="pg-blue" title="Protects you from state mass surveillance programs">:material-eye-outline: State Surveillance</span> - Protection from government agencies, organizations, websites, and services working together to track your activities.
- <span class="pg-brown" title="Protects you from third-party tracking networks">:material-account-cash: Surveillance Capitalism</span> - Protecting yourself from big advertising networks like Google and Facebook, as well as a myriad of other third-party trackers.
- <span class="pg-green" title="Protects your data from being publicly accessible">:material-account-search: Public Exposure</span> - Limiting the information about you online that is accessible to search engines or the general public.
- <span class="pg-blue-gray" title="Protects you from state or corporate censorship">:material-close-outline: Censorship</span> - Avoiding censored access to information and being censored yourself when speaking online.

Some of these threats may weigh more than others. For example, a software developer might have a hacker as their primary threat, but beyond that they would also want privacy from the websites they visit and so on. Likewise, an average Joe may have mass surveillance programs and service provider data access as their primary threat, but beyond that they also need to have decent security to prevent malware from stealing their data.

## Anonymity vs Privacy

<span class="pg-purple" title="Protects your activities from being tied to your real-life identity">:material-incognito: Anonymity</span>

Anonymity is often confused for privacy, but it's a distinct concept. While privacy is a set of choices you make about how your data is used and shared, anonymity is the complete disassociation of your online activities from your real-life identity.

Whistleblowers and journalists, for example, can have a much more extreme threat model requiring total anonymity. That's not only hiding what they do, what data they have, and not getting hacked by hackers or governments, but also hiding who they are entirely. They will sacrifice any kind of convenience if it means protecting their anonymity, privacy, or security, as their lives could depend on it. Most regular people do not need to go so far.

## Privacy From Service Providers

<span class="pg-teal" title="Protects your data from being readable by your service provider">:material-server-network: Service Providers</span>

We live in a world where almost everything is connected to the internet. Our "private" messages, emails, social interactions are typilically stored on a server somewhere. Generally, when you send someone a message, that message is then stored on a server, and when your friend wants to read the message, the server will show it to them.

The obvious problem with this is that the service provider (or a hacker who has compromised the server) can look into your "private" conversations whenever and however they want to do it, without you ever knowing. This applies to many common services like Discord, Telegram, SMS messages, and so on.

Thankfully, end-to-end encryption can alleviate this issue by encrypting communications between parties before they are even sent to the server. The confidentiality of their messages are guaranteed, so long as the service provider does not have access to the user's private key.

??? note "Note on web-based encryption"

    In practice, the effectiveness of different end-to-end encryption implementations varies. Applications such as Signal run natively on the user's system, and every copy of of the application is the same across different installations. If the service provider was to backdoor their applications to try and steal your private keys, that could be detected later using reverse engineering. 
    
    On the other hand, web based end-to-end encryption implementations such as ProtonMail's webmail or Bitwarden's web vault rely on the server dynamically serving Javascript code to the browser to handle cryptographic operations. A malicious server could target a specific user and send them malicious Javascript code to steal their encryption key, and it would be extremely hard for the user to ever notice such a thing. Even if the user does notice the attempt to steal their key, it would be incredibly hard to prove that it is the provider trying to do so, because the server can choose to serve different web clients to different users. 
    
    Therefore, whenever possible you should choose to use native applications which implement end-to-end encryption rather than web clients.

Even with end-to-end encryption, service providers can still profile you based on **metadata**, which is not typically protected. While the service provider could not read your messages to see what you're saying, they can still observe things like who you're talking to, how often you message them, and what times you're typically active. Protection of metadata is fairly uncommon, and you should pay close attention to the technical documentation of the software you are using to see if there is any metadata reduction or protection at all, if that is a concern for you.

## Security and Privacy

<span class="pg-orange" title="Protects you from malware and other passive attacks">:material-bug-outline: Passive Attacks</span>

Security and privacy are often conflated, because you need security to obtain any semblance of privacy—Using tools which appear private is futile if they could easily be exploited by attackers to release your data later. However the inverse is not necessarily true, the most secure service in the world *isn't necessarily* private. The best example of this is trusting data to Google, who have never lost data to breaches and employ industry-leading security experts to secure their services. Even though Google provides a very secure service, very few would consider their data private in their hands.

When it comes to application security, we generally do not (and sometimes cannot) know if the software that we use is malicious, or might one day become malicious. Even with the most trustworthy developers, there is generally no guarantee that their software does not have a serious vulnerability that could later be exploited.

To minimize the potential damage that a malicious piece of software can do, you should employ security by compartmentalization. This could come in the form of using different computers for different jobs, using virtual machines groups of related applications, or using a secure operating system with an strong focus on application sandboxing and mandatory access control.

!!! tip

    Mobile operating systems are generally safer than desktop operating systems when it comes to application sandboxing. Apps cannot obtain root access and only have access to system resources which you grant them.

    Desktop operating systems generally lag behind on proper sandboxing. ChromeOS has similar sandboxing properties to Android, and macOS has opt-in (for developers) sandboxing and strong permissions, however these operating systems do transmit identifying information to their respective OEMs. Linux tends to not submit information to system vendors, but it has poor protection against exploits and malicious apps. This can be mitigated somewhat with specialized distributions which make heavy use of VMs or containers, such as QubesOS.

<span class="pg-red" title="Protects you from malicious agents targeting you specifically">:material-target-account: Targeted Attacks</span>

Targeted attacks against a specific user are more problematic to deal with. Common avenues of attack include sending malicious documents via emails, exploiting vulnerabilities in the browser and operating systems, and physical attacks. If this is a concern for you, you may have to employ more advanced threat mitigation strategies.

!!! tip

    **Web browsers**, **email clients**, and **office applications** all typically run untrusted code sent to you from third-parties by design. Running multiple virtual machines separating applications like these from your main system and each other is one technique you can use to avoid an exploit in these applications from gaining access to the rest of your system. Technologies like QubesOS or Microsoft Defender Application Guard on Windows provide convenient methods to seamlessly do this, for example.

If you are concerned about **physical attacks** you should use an operating system with a verified boot implementation, such as Android, iOS, or macOS. You should also make sure that your drive is encrypted, and that the operating system uses a TPM or Secure Element for rate limiting attempts to enter the encryption passphrase. You should avoid sharing your computer with people you don't trust, because most desktop operating systems do not encrypt data separately per-user.

## Mass Surveillance Programs

Mass surveillance is the surveillance of many or all of a population to monitor that group of citizens. It often refers to government programs such as the ones [disclosed by Edward Snowden in 2013](https://en.wikipedia.org/wiki/Global_surveillance_disclosures_(2013%E2%80%93present)), however it can also be carried out by corporations, either on behalf of government agencies or by their own initiative.

Online, you can be tracked via a wide variety of methods, including but not limited to:

- Your IP address
- Browser cookies
- Data you submit to websites
- Your browser fingerprint
- Payment method correlation

Therefore your goals could be to segregate your online identities from each other, to blend in with other users, and simply to avoid giving out identifying information to anyone as much as possible.

<span class="pg-blue" title="Protects you from state mass surveillance programs">:material-eye-outline: State Surveillance</span>

Governments often cite mass surveillance programs as necessary to combat terrorism and prevent crime, however it is most often used to disproportionately target minorities, political dissidents, and many other groups to create a chilling effect on free speech.

> In the face of [Edward Snowden's disclosures of government programs such as [PRISM](https://en.wikipedia.org/wiki/PRISM) and [Upstream](https://en.wikipedia.org/wiki/Upstream_collection)], intelligence officials also admitted that the NSA had for years been secretly collecting records about virtually every American’s phone calls — who’s calling whom, when those calls are made, and how long they last. This kind of information, when amassed by the NSA day after day, can reveal incredibly sensitive details about people’s lives and associations, such as whether they have called a pastor, an abortion provider, an addiction counselor, or a suicide hotline.[^1]

Despite growing mass surveillance in the United States, the government has found that mass surveillance programs like Section 215 have had "little unique value" with respect to stopping actual crimes or terrorist plots, with efforts largely duplicating the FBI's own targeted surveillance programs.[^2]

<span class="pg-brown" title="Protects you from third-party tracking networks">:material-account-cash: Surveillance Capitalism</span>

> Surveillance capitalism is an economic system centered around the capture and commodification of personal data for the core purpose of profit-making.[^3]

Tracking and surveillance by private corporations is a growing concern for many as well. Massive ad networks operated by Google and Facebook span the internet far beyond just the sites they control, tracking your actions along the way. Using tools like adblockers to block network requests to their servers, and reading privacy policies of the services you use to ensure your data isn't being used or shared for marketing purposes are some effective things you can do to avoid the misuse of your data.

## Limiting Public Information

<span class="pg-green" title="Protects your data from being publicly accessible">:material-account-search: Public Exposure</span>

The best way to ensure your data is private is to simply not put it out there in the first place. Deleting information you can find about yourself online is one of the best first steps you can take to regain your privacy. On sites where you do share information, checking the privacy settings of your account to limit how widely that data is spread is very important. For example, if your accounts have a "private mode", enable it to make sure your account isn't being indexed by search engines and can't be viewed by people you don't vet beforehand.

## Avoiding Censorship

<span class="pg-blue-gray" title="Protects you from state or corporate censorship">:material-close-outline: Censorship</span>

Censorship online can be carried out to varying degrees by actors including totalitarian governments, network administrators, and service providers seeking to control the speech of their users and the information they can access. These efforts to filter the internet will always be incompatible with the ideals of free speech.

Censorship on corporate platforms is increasingly common as platforms like Twitter and Facebook give in to public demand, market pressures, and pressures from government agencies. Government pressures can be covert requests to businesses, such as the White House [requesting the takedown](https://www.nytimes.com/2012/09/17/technology/on-the-web-a-fine-line-on-free-speech-across-globe.html) of a provocative YouTube video; or overt, such as the Chinese government requiring companies to adhere to a strict regime of censorship.

People concerned with the threat of censorship can use technologies like Tor to circumvent it, and support platforms which provide censorship-resistant communication such as Matrix, which has no centralized account authority which can close down accounts arbitrarily.

[^1]: ACLU: [The Privacy Lesson of 9/11: Mass Surveillance is Not the Way Forward](https://www.aclu.org/news/national-security/the-privacy-lesson-of-9-11-mass-surveillance-is-not-the-way-forward)
[^2]: United States Privacy and Civil Liberties Oversight Board: [Report on the Telephone Records Program Conducted under Section 215](https://documents.pclob.gov/prod/Documents/OversightReport/ec542143-1079-424a-84b3-acc354698560/215-Report_on_the_Telephone_Records_Program.pdf)
[^3]: Wikipedia: [Surveillance capitalism](https://en.wikipedia.org/wiki/Surveillance_capitalism)

---
title: "Common Threats"
icon: 'material/eye-outline'
---

Broadly speaking, we categorize our recommendations into these general categories of [threats](threat-modeling.md) or goals that apply to most people. ==You may be concerned with none, one, a few, or all of these possibilities==, and the tools and services you use depend on what your goals are. You may have specific threats outside of these categories as well, which is perfectly fine! The important part is developing an understanding of the benefits and shortcomings of the tools you choose to use, because virtually none of them will protect you from every threat imaginable.

- <span class="pg-purple">:material-incognito: Anonymity</span> - Shielding your online activity from your real-life identity, protecting you from people who are trying to uncover *your* identity specifically
- <span class="pg-red">:material-target-account: Targeted Attacks</span> - Being protected  from dedicated hackers or other malicious agents trying to gain access to *your* data or devices specifically
- <span class="pg-orange">:material-bug-outline: Passive Attacks</span> - Being protected from things like malware, data breaches, and other attacks that are made against many people at once
- <span class="pg-teal">:material-server-network: Service Providers</span> - Protecting your data from service providers, e.g. with end-to-end encryption rendering your data unreadable to the server
- <span class="pg-blue">:material-eye-outline: Mass Surveillance</span> - Protection from government agencies, organizations, websites, and services working together to track your activities
- <span class="pg-brown">:material-account-cash: Surveillance Capitalism</span> - Protecting yourself from big advertising networks like Google and Facebook, as well as a myriad of other third-party data collectors
- <span class="pg-green">:material-account-search: Public Exposure</span> - Limiting the information about you online that is accessible to search engines or the general public
- <span class="pg-blue-gray">:material-close-outline: Censorship</span> - Avoiding censored access to information and being censored yourself when speaking online

Some of these threats may weigh more than others depending on your specific concerns. For example, a software developer with access to valuable or critical data may be primarily concerned with <span class="pg-red">:material-target-account: Targeted Attacks</span>, but beyond that they probably still want to protect their personal data from being swept up in <span class="pg-blue">:material-eye-outline: Mass Surveillance</span> programs. Similarly, an "Average Joe" may be primarily concerned with <span class="pg-green">:material-account-search: Public Exposure</span> of their personal data, but they should still be wary of security-focused issues such as <span class="pg-orange">:material-bug-outline: Passive Attacks</span> like malware affecting their devices.

## Anonymity vs Privacy

<span class="pg-purple">:material-incognito: Anonymity</span>

Anonymity is often confused for privacy, but it's a distinct concept. While privacy is a set of choices you make about how your data is used and shared, anonymity is the complete disassociation of your online activities from your real-life identity.

Whistleblowers and journalists, for example, can have a much more extreme threat model requiring total anonymity. That's not only hiding what they do, what data they have, and not getting hacked by hackers or governments, but also hiding who they are entirely. They will sacrifice any kind of convenience if it means protecting their anonymity, privacy, or security, as their lives could depend on it. Most regular people do not need to go so far.

## Security and Privacy

<span class="pg-orange">:material-bug-outline: Passive Attacks</span>

Security and privacy are often conflated, because you need security to obtain any semblance of privacy: Using tools which appear private is futile if they could easily be exploited by attackers to release your data later. However, the inverse is not necessarily true; the most secure service in the world *isn't necessarily* private. The best example of this is trusting data to Google, who, given their scale, have had minimal security incidents by employing industry-leading security experts to secure their infrastructure. Even though Google provides a very secure service, very few would consider their data private in Google's free consumer products (Gmail, YouTube etc).

When it comes to application security, we generally do not (and sometimes cannot) know if the software that we use is malicious, or might one day become malicious. Even with the most trustworthy developers, there is generally no guarantee that their software does not have a serious vulnerability that could later be exploited.

To minimize the potential damage that a malicious piece of software can do, you should employ security by compartmentalization. This could come in the form of using different computers for different jobs, using virtual machines to separate different groups of related applications, or using a secure operating system with a strong focus on application sandboxing and mandatory access control.

!!! tip

    Mobile operating systems are generally safer than desktop operating systems when it comes to application sandboxing. Apps cannot obtain root access and only have access to system resources which you grant them.

    Desktop operating systems generally lag behind on proper sandboxing. Chrome OS has similar sandboxing properties to Android, and macOS has full system permission control and opt-in (for developers) sandboxing for applications, however these operating systems do transmit identifying information to their respective OEMs. Linux tends to not submit information to system vendors, but it has poor protection against exploits and malicious apps. This can be mitigated somewhat with specialized distributions which make heavy use of virtual machines or containers, such as Qubes OS.

<span class="pg-red">:material-target-account: Targeted Attacks</span>

Targeted attacks against a specific user are more problematic to deal with. Common avenues of attack include sending malicious documents via emails, exploiting vulnerabilities in the browser and operating systems, and physical attacks. If this is a concern for you, you may have to employ more advanced threat mitigation strategies.

!!! tip

    **Web browsers**, **email clients**, and **office applications** all typically run untrusted code sent to you from third-parties by design. Running multiple virtual machines to separate applications like these from your host system as well as each other is one technique you can use to avoid an exploit in these applications from compromising the rest of your system. Technologies like Qubes OS or Microsoft Defender Application Guard on Windows provide convenient methods to do this seamlessly, for example.

If you are concerned about **physical attacks** you should use an operating system with a secure verified boot implementation, such as Android, iOS, macOS, [Windows (with TPM)](https://docs.microsoft.com/en-us/windows/security/information-protection/secure-the-windows-10-boot-process). You should also make sure that your drive is encrypted, and that the operating system uses a TPM or Secure [Enclave](https://support.apple.com/guide/security/secure-enclave-sec59b0b31ff/1/web/1) or [Element](https://developers.google.com/android/security/android-ready-se) for rate limiting attempts to enter the encryption passphrase. You should avoid sharing your computer with people you don't trust, because most desktop operating systems do not encrypt data separately per-user.

## Privacy From Service Providers

<span class="pg-teal">:material-server-network: Service Providers</span>

We live in a world where almost everything is connected to the internet. Our "private" messages, emails, social interactions are typically stored on a server somewhere. Generally, when you send someone a message, that message is then stored on a server, and when your friend wants to read the message, the server will show it to them.

The obvious problem with this is that the service provider (or a hacker who has compromised the server) can look into your "private" conversations whenever and however they want, without you ever knowing. This applies to many common services like SMS messaging, Telegram, Discord, and so on.

Thankfully, end-to-end encryption can alleviate this issue by encrypting communications between you and your desired recipients before they are even sent to the server. The confidentiality of your messages is guaranteed, so long as the service provider does not have access to the private keys of either party.

??? note "Note on web-based encryption"

    In practice, the effectiveness of different end-to-end encryption implementations varies. Applications such as [Signal](../real-time-communication.md#signal) run natively on your device, and every copy of the application is the same across different installations. If the service provider were to backdoor their application in an attempt to steal your private keys, that could later be detected using reverse engineering.

    On the other hand, web based end-to-end encryption implementations such as Proton Mail's webmail or Bitwarden's web vault rely on the server dynamically serving JavaScript code to the browser to handle cryptographic operations. A malicious server could target a specific user and send them malicious JavaScript code to steal their encryption key, and it would be extremely hard for the user to ever notice such a thing. Even if the user does notice the attempt to steal their key, it would be incredibly hard to prove that it is the provider trying to do so, because the server can choose to serve different web clients to different users.

    Therefore, when relying on end-to-end encryption, you should choose to use native applications over web clients whenever possible.

Even with end-to-end encryption, service providers can still profile you based on **metadata**, which is typically not protected. While the service provider could not read your messages to see what you're saying, they can still observe things like who you're talking to, how often you message them, and what times you're typically active. Protection of metadata is fairly uncommon, and you should pay close attention to the technical documentation of the software you are using to see if there is any metadata minimization or protection at all, if that is a concern for you.

## Mass Surveillance Programs

Mass surveillance is an effort to surveil many or all of a given population. It often refers to government programs such as the ones [disclosed by Edward Snowden in 2013](https://en.wikipedia.org/wiki/Global_surveillance_disclosures_(2013%E2%80%93present)). However, it can also be carried out by corporations, either on behalf of government agencies or by their own initiative.

Online, you can be tracked via a wide variety of methods, including but not limited to:

- Your IP address
- Browser cookies
- Data you submit to websites
- Your browser or device fingerprint
- Payment method correlation

Therefore your goals could be to segregate your online identities from each other, to blend in with other users, and to simply avoid giving out identifying information to anyone as much as possible.

<span class="pg-blue">:material-eye-outline: Mass Surveillance</span>

Governments often cite mass surveillance programs as necessary to combat terrorism and prevent crime, however it is most often used to disproportionately target minorities, political dissidents, and many other groups to create a chilling effect on free speech.

!!! quote "ACLU: [The Privacy Lesson of 9/11: Mass Surveillance is Not the Way Forward](https://www.aclu.org/news/national-security/the-privacy-lesson-of-9-11-mass-surveillance-is-not-the-way-forward)"

    In the face of [Edward Snowden's disclosures of government programs such as [PRISM](https://en.wikipedia.org/wiki/PRISM) and [Upstream](https://en.wikipedia.org/wiki/Upstream_collection)], intelligence officials also admitted that the NSA had for years been secretly collecting records about virtually every American’s phone calls — who’s calling whom, when those calls are made, and how long they last. This kind of information, when amassed by the NSA day after day, can reveal incredibly sensitive details about people’s lives and associations, such as whether they have called a pastor, an abortion provider, an addiction counselor, or a suicide hotline.

Despite growing mass surveillance in the United States, the government has found that mass surveillance programs like Section 215 have had "little unique value" with respect to stopping actual crimes or terrorist plots, with efforts largely duplicating the FBI's own targeted surveillance programs.[^1]

<span class="pg-brown">:material-account-cash: Surveillance Capitalism</span>

> Surveillance capitalism is an economic system centered around the capture and commodification of personal data for the core purpose of profit-making.[^2]

Tracking and surveillance by private corporations is a growing concern for many as well. Pervasive ad networks like those operated by Google and Facebook span the internet far beyond just the sites they control, tracking your actions along the way. Using tools like content blockers to limit network requests to their servers, and reading the privacy policies of the services you use can help you avoid many basic adversaries, but can never completely protect you from all tracking.[^3]

Additionally, even companies outside of the ad-tech/tracking space can share your information with [data brokers](https://en.wikipedia.org/wiki/Information_broker) (like Cambridge Analytica, Experian, or Datalogix) or other parties, so you can't automatically assume your data is safe merely because the service you are using doesn't fall within a typical data sharing/tracking category. The strongest protection against corporate data collection is to always encrypt or obfuscate your data whenever possible to make it as difficult as possible for different providers to correlate data with each other and build a profile on you.

## Limiting Public Information

<span class="pg-green">:material-account-search: Public Exposure</span>

The best way to ensure your data is private is to simply not put it out there in the first place. Deleting information you find about yourself online is one of the best first steps you can take to regain your privacy.

- [View our guide on account deletion :hero-arrow-circle-right-fill:](account-deletion.md)

On sites where you do share information, checking the privacy settings of your account to limit how widely that data is spread is very important. For example, if your accounts have a "private mode," enable it to make sure your account isn't being indexed by search engines and can't be viewed by people you don't vet beforehand.

If you have already submitted your real information to a number of sites which shouldn't have it, consider employing disinformation tactics such as submitting fictitious information related to the same online identity to make your real information indistinguishable from the false information.

## Avoiding Censorship

<span class="pg-blue-gray">:material-close-outline: Censorship</span>

Censorship online can be carried out to varying degrees by actors including totalitarian governments, network administrators, and service providers seeking to control the speech of their users and the information they can access. These efforts to filter the internet will always be incompatible with the ideals of free speech.

Censorship on corporate platforms is increasingly common as platforms like Twitter and Facebook give in to public demand, market pressures, and pressures from government agencies. Government pressures can be covert requests to businesses, such as the White House [requesting the takedown](https://www.nytimes.com/2012/09/17/technology/on-the-web-a-fine-line-on-free-speech-across-globe.html) of a provocative YouTube video; or overt, such as the Chinese government requiring companies to adhere to a strict regime of censorship.

People concerned with the threat of censorship can use technologies like Tor to circumvent it, and support platforms which provide censorship-resistant communication such as Matrix, which has no centralized account authority which can close down accounts arbitrarily.

!!! important

    While simply evading censorship itself is relatively easy, hiding the fact that you are evading the censorship system from the censors can be very problematic.

    You should consider what aspects of the network your adversary can observe, and whether you have plausible deniability for your actions. For example, using encrypted DNS can help you bypass rudimentary censorship systems based solely on DNS, but it cannot truly hide what you are visiting from your ISP. A VPN or Tor can help hide what you are visiting from the network administrators, but cannot hide that you are using those networks. Pluggable transports like Obfs4proxy, Meek or Shadowsocks can help you evade firewalls that block common VPN protocols or Tor, but an adversary can still figure out that you are actively trying to bypass their censorship system as opposed to just protecting your privacy through probing or deep packet inspection.

You must always consider the risks involved with trying to bypass censorship, what the potential consequences are, and how sophisticated your adversary may be. Be extra cautious with your software selection, and have a backup plan in case you are caught.

## Common Misconceptions

:material-numeric-1-circle: **Open source software is always secure** or **Proprietary software is more secure**

These myths stem from a number of prejudices, but the source-availability and licensure of a software product does not inherently affect its security in any way. ==Open-source software has the *potential* to be more secure than proprietary software, but there is absolutely no guarantee this is the case.== When you evaluate software, you need to look at the reputation and security of each tool on an individual basis.

Open-source software *can* be audited by third-parties, and is often more transparent regarding potential vulnerabilities than their proprietary counterparts. They can also be more flexible, allowing you to delve into the code and disable any suspicious functionality you find yourself. However, unless you review the code yourself there is no guarantee that code has ever been evaluated, especially with smaller software projects, and the open development process can sometimes be exploited by malicious parties to introduce new vulnerabilities into even large projects.[^4]

On the flip side, proprietary software is less transparent, but that does not imply it is not secure. Major proprietary software projects can be audited internally and by third-party agencies, and independent security researchers can still find vulnerabilities with techniques like reverse engineering.

At the end of the day, it is **vital** that you research and evaluate the privacy and security properties of each piece of software being used, and avoid making decisions based on biases.

:material-numeric-2-circle: **Shifting trust can increase privacy**

We talk about "shifting trust" a lot when discussing solutions like VPNs, which shift the trust you place in your ISP to the VPN provider. While this protects your browsing data from your ISP specifically, the VPN provider you choose still has access to your browsing data: Your data is not yet completely secured from all parties. This means that:

1. You need to exercise caution when choosing a provider to shift trust to, rather than choosing blindly.
2. You still need to employ other techniques like end-to-end encryption to protect your data completely, merely distrusting one provider to trust another is not hiding your data.

:material-numeric-3-circle: **Privacy-focused solutions are inherently trustworthy**

Focusing solely on the privacy policies and marketing of a tool or provider can blind you to its weaknesses. When you're looking for a privacy solution you should determine what the underlying problem is and find technical solutions to that problem. For example, you may want to avoid Google Drive, which gives Google access to all of your data. The underlying problem in this case is a lack of end-to-end encryption, so you should make sure the provider you switch to actually implements end-to-end encryption, or use a tool like Cryptomator which provides end-to-end encryption on any cloud provider. Blindly switching to a "privacy-focused" provider which does not provide end-to-end encryption does not solve your problem, it merely shifts trust from Google to that provider.

The privacy policies and business practices of a provider you choose are very important, but should be considered secondary to technical guarantees of your privacy: Don't elect to merely shift trust to another provider when trusting a provider isn't a requirement at all.

:material-numeric-4-circle: **Complicated is better**

We often see people describing privacy threat models that are overly complex. Often, these solutions include problems like many different email accounts or complicated setups with a lot of moving parts and conditions. The replies are usually answers to, "What is the best way to do X?".

Finding the "best" solution for yourself doesn't necessarily mean you are after an infallible solution with dozens of conditions—these solutions are often difficult to work with realistically. As we discussed previously, security often comes at the cost of convenience. Below, we provide some tips:

1. <mark>Actions need to serve a particular purpose</mark>, think about how to do what you want with the least amount of actions.
2. <mark>Remove human failure points</mark> (don't have a bunch of conditions you must remember to do what with which accounts). Humans fail, they get tired, they forget things... don't have many conditions or manual processes you must remember in order to maintain operational security.
3. <mark>Use the right level of protection for what you intend.</mark> We often see recommendations of so-called law-enforcement, subpoena proof solutions. These require a lot of special case knowledge (knowing about how things truly work under the hood) and are generally not what people want. There is no point in building an intricately anonymous threat model if you can be easily de-anonymized by a simple oversight.

So, how might this look?

One of the clearest threat models is one where people *know who you are* and one where they do not. There will always be situations where you must declare your legal name and places where you can get away without doing so.

1. **Known identity** - A known identity is used for things where you must declare your name. There are many such legal documents and contracts where a legal identity is required. This could range from opening a bank account, signing a property lease, obtaining a passport, a customs declaration when importing an item or otherwise dealing with your Government. These things will usually always lead back credentials such as credit cards, credit rating checks, account numbers and possibly physical addresses.

    We don't suggest using a VPN or Tor for any of these things as your identity is already known through other means.

    !!! tip

        When shopping online, the use of a [parcel locker](https://en.wikipedia.org/wiki/Parcel_locker) can help keep your physical address private.

2. **Unknown identity** - An unknown identity could be a stable pseudonym that you regularly use. It is not anonymous because it doesn't change. If you're a part of an online community you may wish to retain persona that others know. The reason this is not anonymous is because if monitored over a period of time details about the owner may reveal further information, such as the way they write (lingustics), general knowledge about topics of interest etc.

    You may wish to use a VPN for this to mask your IP address. Financial transactions are more difficult and for this we'd suggest using anonymous cryptocurrencies such as Monero. Employing alt-coin shifting may also help disguise where your currency originated. Typically exchanges require KYC (know your customer) to be completed before they will allow you to exchange fiat currency into any kind of cryptocurrency. Local meet-up options may also be a solution, however those often are more expensive and sometimes also require KYC.

3. **Anonymous identity** - Anonymous identities are difficult to maintain over long periods of time for even the most experienced. They should be short-term and short lived identities which are rotated regularly.

    Using Tor can help with this, it's also worth noting greater anonymity is possible through asynchronous (not real time communication). Real time communication is vulnerable to typing analysis patterns more than a slab of text distributed on a forum, email) etc that you've had time to think about, maybe even put through a translator and back again.

[^1]: United States Privacy and Civil Liberties Oversight Board: [Report on the Telephone Records Program Conducted under Section 215](https://documents.pclob.gov/prod/Documents/OversightReport/ec542143-1079-424a-84b3-acc354698560/215-Report_on_the_Telephone_Records_Program.pdf)
[^2]: Wikipedia: [Surveillance capitalism](https://en.wikipedia.org/wiki/Surveillance_capitalism)
[^3]: "[Enumerating badness](https://www.ranum.com/security/computer_security/editorials/dumb/)" (or, "listing all the bad things that we know about") as many adblockers and antivirus programs do, fails to adequately protect you from new and unknown threats because they have not yet been added to the filter list. You need to additionally employ other mitigation techniques to be fully protected.
[^4]: One notable example of this is the [2021 incident in which University of Minnesota researchers introduced three vulnerabilities into the Linux kernel development project](https://cse.umn.edu/cs/linux-incident).

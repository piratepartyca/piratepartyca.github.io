---
title: &#8220;Notice and Notice&#8221; copyright  submission for the Pirate Party with respect to their VPN service
date: 2013-11-07T20:19:35+00:00
author: James Phillips
layout: post
categories: [consultations, copyright, encryption, international-agreements, privacy, tracking]
permalink: /2013/11/07/notice-and-notice-copyright-submission-for-the-pirate-party-with-respect-to-their-vpn-service/
---
Background: <https://my.pirateparty.ca/node/7>{.extern}

## PART 0: Introduction

Greetings,

I am writing on behalf of the Pirate Party of Canada to explain how the &#8220;Notice and Notice&#8221; regime will impact our VPN service (which we discontinued, but plan to bring back).

We are disappointed that we only found out about this through the media. Because the distribution list of the consultation letter is not disclosed, it is difficult to know which stake-holders are being consulted. In general, the Pirate Party of Canada will not operate a VPN service that keeps extensive logs. However, we think a VPN service is important enough that we should still offer one: despite guidance that we should keep detailed logs for 6 months. The primary purpose of our VPN service is to defend human rights: something not possible to do while keeping extensive logs.

While the Pirate Party does not officially condone copyright infringement (especially commercial copyright infringement), I am troubled by the characterization that the _Copyright Modernization Act_ is designed to deter copyright infringement. At it&#8217;s core, copyright is censorship. Authors are given a time-limited monopoly on publishing their work, with the understanding that it must eventually fall into the public domain. All works build on what came before. Technologies like Technological Protection Measures threaten to bring about a second dark age if not handled carefully.

## PART 1: IT details; What is possible?

### A: How reliable is e-mail notification?

E-mail is a &#8220;best effort&#8221; delivery medium. This means that delivery is not guaranteed. This is exacerbated by the SPAM problem: users and hosts may be reluctant to report delivery failure ([[1](#note1)], section 15.4). DMARC allows the sending host to request specific rejection handling, but the receiving host is still free to ignore the advice. One reason a receiving host may want to do this in the context of &#8220;Notice and Notice&#8221; is if a specific host is known for sending poor quality automated infringement notices; while not responding to follow-up e-mail. The person handling such mail for the Pirate Party has requested that we block one such domain as spam.

The mostly standard way of requesting Disposition Notification is described in RFC 3798.[[2](#note2)] By including the Disposition-Notification-To header, the sender is requesting a notification when the message is either opened of deleted (possibly without being read). Again, this is optional on the part of the receiving host. While the government may be tempted to enact regulations requiring intermediaries to respond to such requests, it is a bad idea for the reasons outlined in section 6 of the RFC: &#8220;Security Considerations.&#8221; In particular, &#8220;MDNs do not provide non-repudiation with proof of delivery.&#8221; If non-repudiation is required, registered letter mail should be used instead.

### B: How safe is e-mail notification?

To internet intermediaries and users, entities sending notices of infringement are considered potential attackers. Even if the notice is genuine, internet intermediaries and users must mitigate potential de-anonymization attacks. Among the most common (used by the Pirate Party in it&#8217;s mail-outs), is the use of HTML e-mail including a &#8220;Web Bug.&#8221;[[3](#note3)] A web-bug works by downloading data from the attacker&#8217;s server whenever the message is opened. In the context of a VPN provider, this may reveal the user&#8217;s real IP address if they open a forwarded message from the attacker without the VPN connection being active. Unique URLs included in the message may also be used for de-anonymization.[[4](#note4)] The very nature of infringement notices may make some infringement-specific URLs unavoidable.

The aforementioned attacks can be mitigated by using only plain-text e-mail. However, e-mail attachments are potential attack vectors as well.[[5](#note5)] Extraneous attachments should be avoided. Even if the attached file format is not designed to execute arbitrary code; there have been numerous security vulnerabilities disclosed for most image handling libraries over the years. E-mail software also varies in how it handles the forwarding of attachments. I recommend that to simplify the forwarding of infringement notices to users, plain-text e-mail should be used as much as possible. Copyright holders sending infringement notices may want to consider cryptographically signing their messages as well.

### C: What information is required to identify an alleged infringer?

Our VPN service issues its users RFC 1918 private addresses.[[6](#note6)] Network Address Translation is then used to provide a connection to the IPv4 Internet. This means that in order to have any hope of identifying an alleged infringer, the infringement notice must include: the time, the IP address, and port used by our user. While just the IP address may be enough for traditional ISPs to identify a customer: in the case of our VPN service, the IP address is used by many users at the same time.

If our VPN service ever implements IPv6, it is likely that we will assign our users temporary (randomly generated) addresses. In that case, the full 128 bit address should be sufficient to identify a specific user at any given time. However, in the case of our service, we will not be able to identify specific infringers due to a minimal logging policy. This policy is in place so that users of our service can enjoy the right to privacy: stated explicitly in Article 12 of the _UN declaration of human rights_. It is safer for our users (which may include political dissidents in foreign countries) to keep no logs at all.

## PART 2: Legal details; Will the Pirate Party get deregistered for not keeping logs?

### A: OECD Guidelines on the Protection of Privacy and Transborder Flows of Personal Data

Our minimal logging policy generally follows the _OECD Guidelines on the Protection of Privacy and Transborder Flows of Personal Data_.[[7](#note7)]

We follow the Collection Limitation Principle by limiting the logs we keep. Less data means that the Data Quality Principle is easier to implement.

Because extensive logs have no clear purpose, other than investigating possible abuse, we are following the Purpose Specification Principle. The guideline in question says that &#8220;the purposes for which personal data are collected should be specified not later than at the time of data collection.&#8221; However, it is possible that we may receive a court-order to keep additional logs: while being prohibited from disclosing the logging. The way privacy-conscious services have handled this in other jurisdictions is by partially or completely shutting down the service.[[8](#note8),[9](#note9)] By limiting the logs we keep, we reduce the chances of violating the Use Limitation Principle.

Keeping minimal logs increases the security of the service from a privacy perspective: following the Security Safeguards Principle. By keeping our logging policy simple, we follow the Openness Principle. Minimal logs also reduce the administrative overhead in following the Individual Participation Principle. Simplified logging also simplifies our Accountability to our members: fewer logs mean inevitable mistakes have fewer ramifications in the event of a data-breach.

### B: Explain the difference between criminal and civil liability

_The Copyright Act_[[10](#note10)] sets out two broad classes of remedies: Civil and Criminal. Section 41.27 also allows copyright holders to receive an injunction against the providers of information location tools. While a broad reading of subsection 5 may include keyboards, the VPN service is not really an &#8220;information location tool,&#8221; so that section is not likely to apply.

The following acts appear to have Criminal Remedies:

  * Selling, renting, distributing, exhibiting, or importing infringing copies of a protected work in a manner prejudicial to the owner of the the copyright.
  * Making a plate for making infringing copies or performing a protected work in public for private profit.
  * Circumventing a Technological Protection Measure for commercial purposes.
  * Performing in public for private profit a dramatic, operatic or musical work without permission from the copyright owner.
  * Suppressing the title of or name of the author: of any dramatic, operatic or musical work.

The VPN service is essentially an anonymized Internet connection. While the service may be used by some of its users for the above acts, the service itself is not responsible for such acts. In general, our service is not suitable for commercial copyright infringement because only individual users are allowed to purchase a subscription. Corporations and Unions are prohibited from making donations to the Party by the _Canada Elections Act_.[[11](#note11)] (Section 404(1))

The following acts appear to have Civil Remedies:

  * Infringing copyright
  * Infringement of moral rights (described in sections 14.1 and 17.1).

The _Copyright Modernization Act_[[12](#note12)] introduced section 30.71 that clarifies that incidental buffering is not in itself an infringement of copyright. However, the wording of subsection (b) is troubling because our service has no way of knowing if a specific packet is infringing copyright or not.[[13](#note13)] Even if the packet can be identified as containing a fragment of a copyrighted work, not under a permissive license: one of our users may be making a copy for personal study; a specific exemption under the _Copyright Act_ (section 29). Our service makes use of shared IP addresses, and does not allow our users to forward ports using UPnP. Because of this, our service does not lend itself to seeding infringing content. It is still possible: but any &#8220;downloaders&#8221; would have to have ports forwarded at their end of the connection.

The $5000 to $10,000 statutory damages mentioned in the consultation letter comes from Sections 41.25 and 41.26.

Our interpretation of the wording of subsection 41.26(2)(b) is that we must only retain the records we have at the time of the notice. Because the wording may be interpreted in such a way that logs must be recorded for a period of 6 months or more: we may, out of an abundance of caution, patch our kernel to black-list and log the ports named in any notices.[[14](#note14)] NAT should continue to work with 10,000 or more ports black-listed before we may be forced to allocate a second IP address for our VPN.

### C: It is an infringement of copyright to operate a service solely for the purposes of copyright infringement &#8212; Section 27 Subsections (2.3), (2.4)

Section 8 of the _Canadian Charter of Rights and Freedoms_[[15](#note15)] prohibits unreasonable search or seizure. Due to the shared nature of our VPN service, any logging to track down a specific infringer constitutes an unreasonable search of all of our other users. The only way to universally enforce copyright is to impose a regime of universal surveillance. Universal surveillance prejudices the &#8220;fair dealing&#8221; exemptions outlined in section 29 of the _Copyright Act_.

Fair dealing allows copyright law to avoid conflicting with[[16](#note16)]:

  * The right to freedom of thought, conscience and religion (Article 18)
  * The right to freedom of opinion and expression (Article 19)
  * The right to education (Article 26)
  * The right freely to participate in the cultural life of the community (Article 27)

### D: How does contracting an off-shore provider impact the above?

If we sub-contract to an off-shore provider, any infringement notices would be subject to the laws of the foreign jurisdiction. Since international copyright treaties have wide reach, this would (hopefully) require careful jurisdiction shopping to make sure that the host countries&#8217; laws are not actually more severe than those in Canada. If the regime in Canada becomes too oppressive to maintain a viable VPN service, we may investigate other jurisdictions that actually respect the right to privacy.

## PART 3: References

<a name="note1"></a>[1] Domain-based Message Authentication, Reporting and Conformance (DMARC)
draft-kucherawy-dmarc-base-01
:   <https://datatracker.ietf.org/doc/draft-kucherawy-dmarc-base/?include_text=1>{.extern}

<a name="note2"></a>[2] Message Disposition Notification
:   <https://tools.ietf.org/html/rfc3798>{.extern}

<a name="note3"></a>[3] Wikipedia: Web bug
:   <https://en.wikipedia.org/wiki/Web_bug>{.extern}

<a name="note4"></a>[4] Bitmessage users de-anonymized
:   <http://secupost.net/2325962497/bitmessage-security>{.extern}

<a name="note5"></a>[5] E-mail Viruses
:   <http://www.thegeekprofessor.com/guides/email/email-viruses/>{.extern}

<a name="note6"></a>[6] Address Allocation for Private Internets
:   <https://tools.ietf.org/html/rfc1918>{.extern}

<a name="note7"></a>[7] OECD Guidelines on the Protection of Privacy and Transborder Flows of Personal Data
:   <http://www.oecd.org/internet/ieconomy/oecdguidelinesontheprotectionofprivacyandtransborderflowsofpersonaldata.htm>{.extern}

<a name="note8"></a>[8] Lavabit
:   <http://lavabit.com/>{.extern}

<a name="note9"></a>[9] CryptoSeal VPN shuts down rather than risk NSA demands for crypto keys
:   <http://arstechnica.com/information-technology/2013/10/cryptoseal-vpn-shuts-down-rather-than-risk-nsa-demands-for-crypto-keys/>{.extern}

<a name="note10"></a>[10] Consolidated Copyright Act
:   <http://laws.justice.gc.ca/eng/acts/C-42/>{.extern}

<a name="note11"></a>[11] Canada Elections Act
:   <http://elections.ca/content.aspx?section=res&dir=loi/fel/cea&document=index&lang=e>{.extern}

<a name="note12"></a>[12] Copyright Modernization Act
:   <http://www.parl.gc.ca/HousePublications/Publication.aspx?Language=E&Mode=1&DocId=5697419&File=4>{.extern}

<a name="note13"></a>[13] What Colour are your bits?
:   <http://ansuz.sooke.bc.ca/entry/23>{.extern}

<a name="note14"></a>[14] Reserved network ports
:   <http://lwn.net/Articles/375976/>{.extern}

<a name="note15"></a>[15] Canadian Charter Of Rights And Freedoms
:   <http://laws-lois.justice.gc.ca/eng/Const/page-15.html#h-39>{.extern}

<a name="note16"></a>[16] The Universal Declaration Of Human Rights
:   <http://www.un.org/en/documents/udhr/>{.extern}
---
layout: post
title: Bitcoin and Quantum Computing — An Unpleasant Collision Course
date: 2018-12-29 18:08:00 +0000
summary: Quantum computing will profoundly disrupt Bitcoin and the entire cryptocurrency
  ecosystem. Bitcoin’s developers have a plan for transitioning to quantum-resistant
  cryptography, but their best efforts may not be enough to avert existential risk
  to the network.
categories: jekyll pixyll

---
# Bitcoin and Quantum Computing — An Unpleasant Collision Course

> **_“First movers very rarely win with new technology…because tech becomes obsolete. Tech innovates or it dies.”_**

– _Ari Paul, co-founder/CIO of Blocktower Capital, on Anthony Pompliano’s Off the Chain Podcast, 12/17/18_

***

**Quantum computing will profoundly disrupt Bitcoin and the entire cryptocurrency ecosystem. Bitcoin’s developers have a plan for transitioning to quantum-resistant cryptography, but their best efforts may not be enough to avert existential risk to the network.**

***

**THE GENIUS OF BITCOIN: DISTRIBUTED CRYPTOGRAPHIC CONSENSUS**

**T**he first blockchain blinked into existence on January 3, 2009, when Satoshi Nakamoto’s computer mined the genesis block of bitcoins. Starting with that entry, the entire history of Bitcoin transactions is stored in an ever-growing ledger that can now be found on millions of hard drives worldwide. Other blockchains have sprung up around it, giving rise to a young, thriving technological ecosystem. What began as a revolution in digital money has expanded to distributed computation more generally and is now positioned to be one of the fastest-growing sectors in the global economy over the coming decade.

Bitcoin was the first implementation of digital money that solved the problem of preventing users from spending the same funds more than once without using a centralized database. This is the fundamental innovation of blockchain technology: _distributed consensus._ By recording every transaction on a ledger that is kept by every node on the network, it becomes trivial to achieve agreement among all parties on which funds belong to whom. Each user’s funds are secured by what is known as _public-key cryptography_, which allows the use of public addresses on the ledger that can be viewed by anyone but only allow their respective owners to make transactions. The creator of an address receives a corresponding ‘private key’ that is used to digitally sign transactions from that address.

The security of these digital signatures relies on the existence of mathematical problems that are much harder to solve than their solutions are to check. To crack the so-called Elliptic Curve Digital Signature Algorithm (ECDSA) used by Bitcoin would take today’s fastest supercomputer far over a trillion years. However, in 1999, Peter Shor published an algorithm could do it in ‘polynomial time’, easily on the timescale of hours or minutes \[1\]. The catch is, this algorithm requires a different kind of computer altogether — a _quantum computer_.

***

**QUANTUM COMPUTING WILL DISRUPT CRYPTOCURRENCIES’ DIGITAL SIGNATURE ALGORITHMS**

Quantum Computing may end up being the most significant technology development of the 21st century. Following several decades of slow but steady progress, a bona fide technological arms race has now begun. With QC on the verge of reaching utility at a large scale, superpowers like the USA, China, and the EU have invested billions of dollars into research and development \[2, 3\]. The world’s largest technology corporations have also sprung into competition on this frontier, including Google, IBM, Microsoft, Intel, and Alibaba. What used to be a niche area of physics is becoming replete with entrepreneurs and scientists determined to carve out of a slice of this emerging sector for themselves. Massive value will accrue to the winners in the race to build the world’s largest and most effective quantum computer.

The alarm has begun to be raised about the approaching downfall of modern cryptographic standards. Digital signature algorithms such as ECDSA and the closely related RSA secure not only Bitcoin and cryptocurrencies but the entire internet, banking system, and more. The issue has been covered by [the Economist](https://www.economist.com/science-and-technology/2018/10/20/quantum-computers-will-break-the-encryption-that-protects-the-internet) \[4\], [Fortune](http://fortune.com/2018/12/15/quantum-computer-security-encryption/) \[5\], and [the New York Times](https://www.nytimes.com/2018/12/03/technology/quantum-encryption.html) \[6\]. While large-scale quantum computers appear to still be at least five years out, major governmental institutions such as the NSA are already beginning their transition to post-quantum standards \[7\]. The United States’ National Institute of Standards and Technology, or NIST, has stated that “regardless of whether we can estimate the exact time of the arrival of the quantum computing era, we must begin now to prepare our information security systems to be able to resist quantum computing”. Several scientific articles have gone further into detail on the nature of the threat specifically to Bitcoin and blockchains \[8, 9\], including a recent [Nature commentary](https://www.nature.com/articles/d41586-018-07449-z) \[11\].

The response in the cryptocurrency community, however, has so far been muted. While several luminaries in the field, including Vitalik Buterin and Andreas Antonopoulos, have briefly addressed the issue \[12, 13\], we will see below how their statements fail to account for the full scope of the problem at hand. In the remainder of this article, we will critically examine the current state of thinking around Bitcoin’s eventual migration to post-quantum cryptography.

***

**_KR: “Andreas, I want to ask you one last question, and it’s one that really scares the shit out of me, and that is quantum computing. It seems like every other week I’m hearing some press about quantum computing, and how they’re making giant leaps forward. Doesn’t quantum computing and this idea of being able to potentially crack the encryption that underpins all of these cryptocurrencies … is that going to be a reality in the next ten to twenty years?”_**

**_AA: “Absolutely. It is going to be a reality.”_**

**_— Kevin Rose & Andreas Antonopoulos, on the Kevin Rose Podcast, 11/13/17_**

***

**THE NATURE OF THE PROBLEM**

The most obvious explanation for the lack of clamor around this topic in the world of cryptocurrencies is an understandable ignorance that it is even worth discussing in the first place. However, for those investors, developers, and enthusiasts who have stumbled across mentions of quantum computing’s role in the future of cryptocurrency, the line of thinking may instead be something like, _“Bitcoin’s developers have already thought about this and have a plan to take care of it when the time comes.”_ Is that really the case? Let’s see how the core developers themselves think about the subject.

A discussion on the Bitcoin dev forum titled ‘[Transition to post-quantum](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-February/015761.html)’ began on February 15, 2017, with core developers Tristan Hoy and Tim Ruffing laying out the plans for what is known as a _commit-delay-reveal_transaction scheme \[14\]. Adam Back, renowned cryptographer and Blockstream CEO, has proposed a similar mechanism \[15\].

To understand what this entails, we must first appreciate the specific threat this method is meant to combat.

The essential problem is this. If Bitcoin changes nothing, then eventually, addresses with known public keys will have their private keys derived from those public keys by a quantum computer running Shor’s algorithm. This includes very old addresses (including Satoshi’s) as well as addresses that have sent a transaction, publishing their public keys to the blockchain. The owner of that quantum computer could then simply use the found private keys to send bitcoin from those addresses to themselves. A transition to a post-quantum digital signature algorithm does not solve this problem; an attacker could simply use the vulnerability to claim balances on the new chain using the old-format private keys. An alternative method of attack would be to short bitcoin and then make this vulnerability public, crashing the value of bitcoin and enriching themselves in the process.

The commit-delay-reveal scheme is meant to help Bitcoin address these challenges. It works as follows: a user can create a wallet secured by a post-quantum signature algorithm, then publish a transaction to the blockchain using a combination of their old private key, the new private key from that post-quantum address, and a predefined delay period (which the authors in \[10\] suggest should be approximately 6 months). The transaction would then go through after that period of time.

That is the most rigorous solution available. Unfortunately, it has several crucial flaws: first, not only do those become funds unusable for a long period of time, but the process significantly bloats the blockchain \[14\] and may be too technically challenging to be performed by less savvy holders of bitcoin. Second, whether a commit-delay-reveal scheme is implemented or not, bitcoin residing in vulnerable addresses with lost private keys will be stolen anyways. Ultimately, those funds can still be dumped on the market by an attacker who simultaneously shorts bitcoin, as enumerated above.

Bitcoin’s developers have also considered stopgap measures. A bitcoin-dev [discussion ](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-December/016556.html)from December 14th, 2018 \[16\] suggests including the capability of generating addresses based on higher-bit (e.g., 381-bit instead of 256-bit) elliptic curves, which would require about 150% as many qubits as the present curves to efficiently crack via Shor’s algorithm. Of course, these measures fail to solve the fundamental problem of relying on elliptic-curve digital signatures. Like the commit-delay-reveal scheme, these mechanisms also rely on individual users opting in to using the more secure signatures, leaving millions of bitcoins behind in vulnerable addresses.

This threat may end up being existential. It is also not limited to Bitcoin — indeed, it imperils the future of nearly every single cryptocurrency in existence today. In order to be immune to quantum computing attacks, a cryptocurrency must have utilized a post-quantum signature algorithm from its inception. Several examples already exist, and more will inevitably follow in the years to come. Heavily centralized altcoin projects may also have a fighting chance to make it over this hump.

***

**HOW LONG DO WE HAVE?**

The number of _logical qubits_ required to crack secp256k1, the specific elliptic curve on which Bitcoin’s public-key cryptography is based, is approximately 2330 \[17\]. The noisiness associated with qubits, however, means that the number of qubits in a quantum computer is larger than the number of logical qubits that it functionally possesses. A scientific paper by Aggarwal et al. (2017) modeled the development of quantum computing given optimistic and conservative assumptions, respectively; this model estimates that 2330 logical qubits will be available between approximately 2024 and 2030. If higher-bit elliptic curves are used as a stopgap, it will shift Bitcoin’s security window by a year or two. Eventually, though, the blockchain’s ability to support more complex curves will be outstripped by the exponentially-growing computational abilities of quantum computers.

***

**Further Reading**: [https://medium.com/coinmonks/quantum-computers-pose-a-credible-threat-to-the-security-of-bitcoin-4b1dd65944ca](https://medium.com/coinmonks/quantum-computers-pose-a-credible-threat-to-the-security-of-bitcoin-4b1dd65944ca "https://medium.com/coinmonks/quantum-computers-pose-a-credible-threat-to-the-security-of-bitcoin-4b1dd65944ca")

***

**APPENDIX A — CRITICAL EVALUATION OF ANDREAS’ AND VITALIK’S ATTEMPTS TO ADDRESS THIS ISSUE**

Andreas Antonopoulos has addressed the threat of quantum computers to cryptocurrencies several times [(KR podcast](https://www.kevinrose.com/single-post/andreas-antonopolous)), ([YouTube Video](https://www.youtube.com/watch?v=wlzJyp3Qm7s)). In the rest of the interview quoted above, Andreas goes on to say that cryptocurrencies may be “the least of our worries” when it comes to quantum computing. Specifically, he delineates _unequal_ _availability_ of quantum computing as the major threat. His ultimate proposed solution to the problem, however, is just that the algorithm can be changed whenever it becomes necessary. This article has made it clear why it will be anything but straightforward to do so.

Vitalik Buterin has also addressed the threat of quantum computers in an incredibly prescient [article ](https://bitcoinmagazine.com/articles/bitcoin-is-not-quantum-safe-and-how-we-can-fix-1375242150/)entitled “Bitcoin is not quantum-safe, and how we can fix it when needed”. To quote from his article, he states:

_“The solution is this: as soon as a quantum pre-emergency is declared, everyone should move their wealth into a 1-of-2 multisignature transaction between an unused, old-style, Bitcoin address, and an address generated with the new Lamport scheme. Then, developers should quickly create the Lamport patch for as many Bitcoin clients as possible and push for everyone to upgrade. If the whole process is done within weeks, then by the time quantum computers become a threat the bulk of people’s bitcoins will be in new-style Lamport addresses and will be safe.”_

This assumes that everyone both can and will move their bitcoin to new wallets. As mentioned above, this will not be possible for wallets whose private keys have been lost, or for users who are unable or unwilling at the time to respond in such a manner. The commit-delay-reveal scheme being considered by Bitcoin’s developers is a more evolved (and less centralized) solution than what Vitalik articulates, and it still has the problems that are discussed above.

***

**WORKS CITED**

1\. Shor, P.W., _Polynomial-time algorithms for prime factorization and discrete logarithms on a quantum computer._ SIAM review, 1999. **41**(2): p. 303–332.

2\. Castelvecchi, D., _Europe Shows First Cards in €1-billion Quantum Bet._ 2018.

3\. McFarland, M. _China bet big on quantum computing. Now the US races to keep up._ 2018 12/20/2018\].

4\. _Quantum computers will break the encryption that protects the internet_, in _The Economist_. 2018.

5\. Hackett, R., _Quantum Computers Threaten the Web’s Security. We Must Take Action Now_, in _Fortune_. 2018.

6\. Cade Metz, R.Z., _The Race Is On to Protect Data From the Next Leap in Computers. And China Has the Lead._, in _The New York Times_. 2018.

7\. Schneier, B. _NSA Plans for a Post-Quantum World_. 2015; Available from: [https://www.schneier.com/blog/archives/2015/08/nsa_plans_for_a.html](https://www.schneier.com/blog/archives/2015/08/nsa_plans_for_a.html "https://www.schneier.com/blog/archives/2015/08/nsa_plans_for_a.html")

8\. _Post-Quantum Cryptography_. December 17, 2018; Available from: [https://csrc.nist.gov/projects/post-quantum-cryptography.](https://csrc.nist.gov/projects/post-quantum-cryptography "https://csrc.nist.gov/projects/post-quantum-cryptography")

9\. Aggarwal, D., et al., _Quantum attacks on Bitcoin, and how to protect against them._ arXiv preprint arXiv:1710.10377, 2017.

10\. Stewart, I., et al., _Committing to quantum resistance: a slow defence for Bitcoin against a fast quantum computing attack._ Royal Society open science, 2018. **5**(6): p. 180410.

11\. Fedorov, A.K., E.O. Kiktenko, and A.I. Lvovsky, _Quantum computers put blockchain security at risk_. 2018, Nature Publishing Group.

12\. Antonopoulos, A., _Bitcoin Q&A: Is quantum computing a threat?_ 2018, YouTube.

13\. Buterin, V. _Bitcoin Is Not Quantum-Safe, And How We Can Fix It When Needed_. 2013; Available from: [https://bitcoinmagazine.com/articles/bitcoin-is-not-quantum-safe-and-how-we-can-fix-1375242150/.](https://bitcoinmagazine.com/articles/bitcoin-is-not-quantum-safe-and-how-we-can-fix-1375242150/ "https://bitcoinmagazine.com/articles/bitcoin-is-not-quantum-safe-and-how-we-can-fix-1375242150/")

14\. Hoy, T. and T. Ruffing. _\[bitcoin-dev\] Transition to post-quantum_. 2018 12/20/18\]; Available from: [https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-February/015715.html.](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-February/015715.html "https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-February/015715.html")

15\. Back, A. 12/20/18\]; Available from: [https://twitter.com/adam3us/status/948219461345075201](https://twitter.com/adam3us/status/948219461345075201 "https://twitter.com/adam3us/status/948219461345075201").

16\. Towns, A. _\[bitcoin-dev\] Schnorr and taproot (etc) upgrade_. 2018; Available from: [https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-December/016556.html.](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-December/016556.html "https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-December/016556.html")

17\. Roetteler, M., et al. _Quantum resource estimates for computing elliptic curve discrete logarithms_. in _International Conference on the Theory and Application of Cryptology and Information Security_. 2017. Springer.
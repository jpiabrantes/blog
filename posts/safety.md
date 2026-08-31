---
template: post
title: We already keep the world safe from AGI (humans). Let’s do the same for AI.
slug: keep-the-world-safe-from-ai
draft: false
date: 2026-08-31T00:00:00.000Z
description: >-
  AI safety today stops when training ends. Humans are kept safe by identity, memory and real consequences for life. A concrete proposal (httpi, automatic courts) to do the same for AI.
category: artificial-intelligence
tags:
  - artificial-intelligence
  - AI safety
---

AI safety today is mostly about training: teach the model to do more “good” and less “bad”.

We also educate children to be well behaved. But that is not what keeps the world safe from humans (AGI). The real safety mechanisms kick in after training is done (and you are of age): we give more resources to people who do “good” and take them away from people who do “bad”.

AI safety should be more about the latter. AI brings new risks, but taking inspiration from what already works for humans is an excellent start.

## How do we keep the world safe from humans?

If you misbehave you lose money (a fine) or time (jail) or both. For that to work we need two things: know who did it (credit assignment), and be able to punish them. Humans build this into every interaction, so that misbehaving costs more than the damage done. To rent a room or a car you show your ID or leave a deposit. To sell to other people you register a business.

We know this works. The famous prisoner’s dilemma is solved once players have memory and can identify each other.

## How to apply this to AI?

I am diving right into a concrete and crazy idea, however, I am trusting you to be smart and extract the general principles instead of focusing on the exact tunable parameters:

### httpi: a new protocol

https does two jobs. It proves the server is who it says it is (it had to register and get a certificate), and it stops anyone else from listening.

httpi adds a third job: the client has to prove who it is too. Logins already do this, but every service has its own. In httpi there is one identity layer shared by everyone, like https already does for servers, and only two kinds of identity: human or business. A business is just a weighted list of humans (its shareholders).

Every human gets a free rate limit. Businesses don’t: they need a deposit. Anyone, human or business, can deposit more to raise their limit.

Both sides keep logs of every interaction for a few days. If someone misbehaves, the logs go to an automatic court (more on that below), which can lower their rate limit or take their deposit.

Punishment takes the deposit first. If the harm is bigger than the deposit, the rest lands on the humans behind the business, in proportion to their share, and through them on every other business they own. You can’t hide behind a new business.

Services that don’t use httpi can’t identify or punish bad actors, so malicious agents will attack them first. Over time that pushes everyone onto httpi.

### Automatic courts

Everyone on httpi is judged by the same short set of rules, written in plain English. A constitution. For example, rule one: do not cause human pain.

If your logs show someone broke a rule, you submit a case with the logs as proof. The other side is notified and gets time to submit their own.

Then several independent AIs look at the proofs and the reputation of both parties, and bet on one question: what would a human judge decide? Usually the most likely answer becomes the verdict. But sometimes, with probability proportional to how serious the case is, real human judges decide. That keeps the AIs honest: bet wrong and you lose money. (Vitalik Buterin describes this mechanism [here](https://vitalik.eth.limo/general/2024/11/09/infofinance.html#info-finance-for-distilled-human-judgement).)

If the logs show a real crime, the identities are revealed and the humans behind them face their own country’s law. But the main point of automatic courts is that they are as fast as the AIs they judge.

### Automatic contracts

Using httpi is signing a standard contract. The terms are always the same: I sign the messages I send, I keep logs, I accept the court’s verdict. Every request is a handshake on those terms.

We can also imagine custom contracts that could be judged by the same automatic courts. But the internet is already full of custom terms and custom logins, and that is exactly why each service is vulnerable in its own way. The value of httpi is that there is a standard contract and identity.

## The general principle

None of the details above matter much. What matters is this: today we are focused on training, where we use fake signals of pleasure and pain. We need to step up: real consequences, real credit assignment, more compute for the ones who do good and less for the ones who do harm.

## Common doubts

**A human prompts an AI. Whose identity is used, the human’s or the company’s?**

If the AI runs on the human’s computer, the human’s. If it runs on a company’s server, the company’s.

Say you use Claude Code. You prompt Claude over httpi. Claude then makes **your computer** call another service over httpi, so the call carries **your identity**, and that service gets hacked. The service takes you to court, because as far as it can see, you did it. You get notified, check your logs, and see that your prompt was within the rules: it was Claude that misbehaved. You add those logs to the case. Claude gets punished (a fine, or a lower rate limit), the case goes public, and some users leave Claude.

**If everyone has to identify, there is no privacy.**

There is a lot of work on proving things about yourself without revealing who you are (see zero-knowledge proofs). Here you only need to prove a few things: I am a human, I have this deposit, I have this rate limit.

**People will sell their identities, or get them stolen.**

Yes. That is why a human identity alone has a rate limit, and raising it needs a deposit. To avoid identities (private keys) being stolen, there could be a small reward for whoever proves they own a private key that isn’t theirs. Leaks would be found quickly and the affected keys rotated.

**A badly trained AI doesn’t care about fines.**

Two things. First, the people who run the AI care, because they are the ones being fined. Second, an AI with no rate limit can do no harm, and a ban, from an automated court, is just a rate limit of zero.

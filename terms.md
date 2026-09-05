---
title: "Terms of Service — paygate"
description: "The terms governing use of paygate: custody, settlement, finality, fees, data and the limits of what the service can promise."
source: "https://paygatehq.com/terms"
---

Legal

# Terms of Service

Effective 2026-09-06 · These terms govern use of the paygate payment gateway by a merchant.

Version 2026-09-06.3

Legal review

These terms are in force and binding, and they have not had a line-by-line legal review. Each section below is marked with how much review it has actually had:

-   \[counsel-approved\] — §24 and §25, the disclaimer and the limitation of liability. Reviewed and approved by counsel on 2026-08-29.
-   \[counsel-directed\] — §1, §28 and §29. Counsel instructed what these had to say on 2026-08-28 and they were rewritten to match, but the wording is ours.
-   \[technical account\] — the remaining 26 sections. Written by the people who wrote the code, and accurate about what the software does. No lawyer has read them.

We would rather say which is which than let the document imply a review it has not had.

In short

The document below is what binds. This is what most people would want to know before reading it, and each line points at the section it comes from.

-   [§7](#custody-escrow) — We never hold your money in an account of ours. A payment rests in an escrow contract for your refund window, then releases to the payout address you registered.
-   [§9](#operator-powers) — We cannot return a payer's money, freeze funds, or send them anywhere else. Neither exit from the contract takes a destination, and this deployment holds no key that could change that.
-   [§10](#finality) — A payment reported as paid can still reverse if the chain reorganises. If you shipped on paid, that loss is yours.
-   [§3](#preview) — Under these standard terms nothing is owed to you when a published objective is missed; an enterprise agreement can carry a service level. The escrow contract was independently audited in September 2026 and all nine findings are fixed. If a chain cannot be watched the checkout stops taking new payments on it, and money already on the contract can be released by you, from any wallet, without us.
-   [§21](#not-screened) — We do not screen payers, wallet addresses, or where money came from — against sanctions lists or anything else. Those obligations remain yours.
-   [§31](#acceptable-use) — You promise not to use paygate for fraud, for unlawful goods, or to launder money. If you do, we can suspend your account and refuse to verify your identity documents again.
-   [§25](#liability) — Our liability to you is capped at the fees you paid us in the three months before the claim.
-   [§27](#changes) — When these terms change you will be asked to accept the new version before you can carry on using the console.

## Contents

1.  [1. Parties](#parties)\[counsel-directed\]
2.  [2. Definitions](#definitions)\[technical account\]
3.  [3. What the service does not do yet](#preview)\[technical account\]
4.  [4. Eligibility and account information](#eligibility)\[technical account\]
5.  [5. Test mode and live mode](#modes)\[technical account\]
6.  [6. Funds: where your money is](#custody)\[technical account\]
7.  [7. Funds: the escrow contract](#custody-escrow)\[technical account\]
8.  [8. Refunds and returns](#refunds)\[technical account\]
9.  [9. What our operators can and cannot do](#operator-powers)\[technical account\]
10.  [10. Finality and reversal](#finality)\[technical account\]
11.  [11. Wrong-chain and unmatched transfers](#wrong-chain)\[technical account\]
12.  [12. Subscriptions and mandates](#mandates)\[technical account\]
13.  [13. Fees](#fees)\[technical account\]
14.  [14. API keys](#api-keys)\[technical account\]
15.  [15. Authentication and sessions](#sessions)\[technical account\]
16.  [16. Idempotency](#idempotency)\[technical account\]
17.  [17. Webhooks](#webhooks)\[technical account\]
18.  [18. Rate limits and acceptable use](#rate-limits)\[technical account\]
19.  [19. Your customers’ data](#end-customer-data)\[technical account\]
20.  [20. Identity verification](#identity-verification)\[technical account\]
21.  [21. What is not screened](#not-screened)\[technical account\]
22.  [22. Records, retention and deletion](#retention)\[technical account\]
23.  [23. Availability, suspension and termination](#availability)\[technical account\]
24.  [24. Disclaimers](#disclaimers)\[counsel-approved\]
25.  [25. Limitation of liability](#liability)\[counsel-approved\]
26.  [26. Indemnity](#indemnity)\[technical account\]
27.  [27. Changes to these terms](#changes)\[technical account\]
28.  [28. Governing law and disputes](#governing-law)\[counsel-directed\]
29.  [29. Contact](#contact)\[counsel-directed\]
30.  [30. Privacy](#privacy)\[technical account\]
31.  [31. Acceptable use](#acceptable-use)\[technical account\]

## 1. Parties\[counsel-directed\]

These terms are an agreement between you (“you”, “the merchant”) and paygate (“we”, “us”, “paygate”). They govern your use of the paygate API, the merchant console, the hosted checkout pages, the developer portal and everything else we operate under the paygate name (together, “the service”).

**paygate is a product name, not a registered company.** The service is operated under that name, including for live payments. If it later moves under a registered entity, these terms will change under §27 and you will be asked to accept the new version.

You accept these terms when you create an account or use the service, whichever happens first. If you are accepting on behalf of a company, you confirm you are authorised to bind it.

## 2. Definitions\[technical account\]

-   **Payer** — your customer. A payer is never our customer, and we have no direct relationship with them.
-   **Live mode** and **test mode** — the two modes the service runs in. Which one a request runs in is determined by the API key it was made with.
-   **Deposit address** — the blockchain address a payer sends funds to for a given payment.
-   **Escrow** — the on-chain contract used by the escrow settlement path described in §7.
-   **Hold** — the interval between funds leaving a payer and reaching a merchant, on the escrow path. Its length is the hold period configured for the product.
-   **Mandate** — a payer’s on-chain authorisation permitting charges up to a fixed cap per period, described in §12.
-   **Reversal** — a payment previously reported as paid becoming unpaid, because the blockchain reorganised. See §10.

## 3. What the service does not do yet\[technical account\]

**This is a new payment processor, and these are the things it does not do yet.** Specifically, and without qualification:

-   The escrow contract described in §7 was independently audited in September 2026. The audit found nine issues, three of them high severity, and all nine are fixed in the contract this service runs against. The audited source is identified by content hash in our repository, so the version reviewed is not a matter of trust. It is the contract every subscription settles through.
-   These standard terms carry no uptime commitment — an enterprise agreement is negotiated separately and can carry one (§23). Under these terms, what decides your exposure is what the system does when something breaks, and that is built rather than promised. New payments **fail closed**: when a chain cannot be watched, the checkout page refuses to show an address for it rather than inviting a transfer nothing would see. Money already on the contract stays **recoverable without us**: `collect` and `releaseHold` are permissionless and not pausable, so a payment this gateway cannot settle is one you can settle yourself, from any wallet, without our key and without our permission.
-   Backups are taken and each one is verified by restoring it and checking the ledger still balances. That is a procedure, not an undertaking about how much data a failure could cost you.

The status page publishes what the service is measured against and what it is currently doing. Those are objectives, not undertakings.

Every other section of these terms is read subject to this one. Judge what the service is fit for on the facts above rather than on our confidence in it: the audit, the fail-closed behaviour and the permissionless recovery are all things you can verify yourself, on-chain and in our repository, without taking our word for any of them.

## 4. Eligibility and account information\[technical account\]

You must provide accurate account information and keep it current. Where identity verification is enabled (§20), you provide and warrant the accuracy of your legal name, your country of registration, and — for a business — your company name and registration number, and you record your consent at the point you submit them.

You are responsible for determining whether accepting cryptocurrency payments is lawful for you, in your jurisdiction, for the goods and services you sell. We do not make that determination for you and nothing in the service should be read as advice that it is.

## 5. Test mode and live mode\[technical account\]

The mode is carried by the credential, not by a header or a setting: a key beginning `sk_test_` operates in test mode and a key beginning `sk_live_` operates in live mode. A key cannot cross between them.

**Test-mode payments, balances, charges and settlements are simulated and are not money.** Nothing that happens in test mode creates an obligation on us, on you, or on anyone else to pay anything.

## 6. Funds: where your money is\[technical account\]

**Every payment reaches you the same way.** Your customer sends to a deposit address generated for that one payment, so what arrives is credited to it whatever the amount. The funds are swept into the escrow contract described in §7, held there for the refund window in §8, and then released to the payout address you registered — less any fee under §13.

You register that payout address yourself and it is the only destination the contract will release to. There is no balance held in an account of ours, no withdrawal to request, and no step where money waits on a decision by us.

## 7. Funds: the escrow contract\[technical account\]

Under **escrow settlement** — the strategy named `escrow_contract` — the payer sends to a deposit address generated for that payment. The funds are then swept into the escrow contract, where they rest for the configured hold period before being released to the payout address you registered, net of any fee under §13.

**While the funds rest there, this is what we can and cannot do.**

-   **We cannot send them anywhere but your address.** `releaseHold` pays the payout address recorded on your account and takes no destination argument.
-   **We cannot stop them reaching you.** `releaseHold` is permissionless and not pausable: once the hold matures, you — or anyone — can push it from any wallet, without our key and without our permission.
-   **We cannot return them to your payer.** Only the controller key on your account can refund a hold. That key is yours.
-   **We can change the payout address on your account, and we can deactivate the account, which delays a release.** The first exists so a merchant who loses their controller key can still be paid; the second is an offboarding and fraud control. Both require the contract owner key. Neither is reachable with the key this gateway runs with day to day, so an attacker holding the operator key can do neither.

We describe that last power as custody, because it is one: an address we can change is an address you have not solely controlled. We do not describe the service as non-custodial, and you should not either.

Two consequences worth stating plainly. First, until the sweep completes, a payment reading `paid` is true of your customer and not yet of you — the money has left them and has not reached you. Second, **this is the only path.** One-time payments and subscriptions both settle through this contract; the recurring mechanism in §12 requires it, and there is no non-custodial route for either.

## 8. Refunds and returns\[technical account\]

The hold period _is_ the refund policy. It is the interval in which returning funds to a payer is something you can perform through the contract rather than merely request.

For a **one-time payment** the window is fixed by us and is the same for every account. It is not a setting, because it is what we can tell a payer before they send: a window that varied by merchant could not be stated at all. For a **subscription** it comes from the price the customer is on, which carries its own refund policy and, where that policy is a full window, its own length.

Once a hold is released to you, there is no mechanism to reverse it. A card network has chargebacks; a blockchain has nothing. Any obligation you have to refund a customer beyond these limits is yours to discharge from your own funds.

## 9. What our operators can and cannot do\[technical account\]

While funds are held under §7, our operators can release them to you. That power is not a privilege of ours: releasing a matured hold is permissionless, so you can do it yourself and so can anyone — we do it because it is convenient, not because only we can.

**We cannot return held funds to the payer.** The escrow admits only your own controller key for a return. The branch that let our keys do it is disabled deliberately, so that no key we hold can move a payer’s money. If returning a payment is the right outcome, the console gives you the transaction and your own wallet signs it.

This is a limit on us rather than on you, and it is the point: there is no operator of ours, and no combination of operators, who can move money out of a hold. The contract owner key is a separate thing and it is not unlimited either — §7 lists exactly what it can do. It also means the decision is yours to make and yours to be accountable for. See §8.

Every operator action of this kind writes a permanent audit record. Those records cannot be edited or deleted — see §22.

## 10. Finality and reversal\[technical account\]

**A payment reported as `paid` is not final.** `paid` means a confirmation threshold was reached, which is a probability statement about a blockchain and not a settlement guarantee.

If the chain reorganises more deeply than the confirmation window, a payment moves to `reversed` and a `payment.reversed` event is emitted. If you released goods or services on `paid`, that loss is yours. You should handle `payment.reversed` before you ship, and you can rehearse it in test mode — the service can simulate a reorg on demand.

[The payments guide](https://developer.paygatehq.com/docs/payments) describes the full lifecycle, including under-payment, over-payment, late payment and expiry.

## 11. Wrong-chain and unmatched transfers\[technical account\]

BNB Smart Chain and Ethereum share an address format. A payer who sends USDT on the wrong chain sends it to an address that looks correct and is not, and **those funds are generally unrecoverable — by us, by you, or by anyone.**

A transfer sent to an address this service does not watch is not a payment and cannot become one. Transfers we do observe are recorded with their originating address, and where one cannot be attributed it is kept with the reason rather than discarded. But recording is not recovery, and we promise no recovery.

## 12. Subscriptions and mandates\[technical account\]

A blockchain has no direct debit. A subscription here is therefore a cap your payer signs once, over a vault your payer funds: they authorise charges of at most a fixed amount per period, and each period you may charge up to that cap and no further. The cap is enforced on-chain and not merely in our software.

**A payer can revoke a mandate themselves, on-chain, without your cooperation or ours.** Neither of us can prevent that, and neither of us can charge after it. A mandate can also fail for want of funds in the vault, which is a state you handle rather than an error we resolve.

Prices are immutable once created — they are archived rather than edited — so an existing subscriber is never repriced without a new agreement.

## 13. Fees\[technical account\]

A platform fee may be applied to settlement. It is set per account by us and is not a setting you can change. Where the escrow path is used, the contract itself bounds what can be taken: the proportional fee cannot exceed ten per cent, and any flat component is bounded by a separate limit set in the contract.

**The fee that applies to your account is the one shown in your console** and on the [pricing page](/pricing). No figure appears in this document, because a figure here would be a second source of truth for a number that is per-account.

Blockchain transaction costs are separate from any fee and are borne as the deployment is configured. Ask before you rely on a particular arrangement.

## 14. API keys\[technical account\]

API keys are hashed on arrival and are not recoverable. The plaintext is displayed exactly once, at creation; we retain only a short prefix so a key can be identified in a list. If you lose a key, we cannot return it to you — create a new one and revoke the old.

**Scopes limit keys, not people.** A key can be restricted to what one integration needs. A console sign-in holds every scope, because it is you. Do not mistake a scope for a permission model over your staff.

You are responsible for the custody of your keys and for everything done with them. A request carrying your key is your request.

## 15. Authentication and sessions\[technical account\]

Account passwords are stored using argon2id and are not recoverable by us. Console sessions are recorded server-side so they can be revoked, and the record holds a user-agent string and an IP address and nothing further. It is deliberately coarse: it is a session list you can act on, not a device fingerprint.

Our own operator accounts require a second factor and hold non-renewing eight-hour sessions.

## 16. Idempotency\[technical account\]

Every request that changes state requires an `Idempotency-Key`. A repeated key replays the stored response rather than performing the operation again, so a retry after a timeout cannot create a second payment.

You must send a key that is stable for one logical operation and distinct across different ones. Reusing a key across two different operations returns you the first one’s response, and that is your error rather than a defect. [The idempotency guide](https://developer.paygatehq.com/docs/idempotency) covers the contract in full.

## 17. Webhooks\[technical account\]

Events are delivered to endpoints you register. Each delivery is HMAC-signed with a signed timestamp; delivery is **at least once**, retried for approximately two days, and then parked in a dead-letter queue you can inspect and replay from. An endpoint that keeps failing is disabled, and we tell you.

You must:

-   verify the signature on every delivery, and reject anything that fails;
-   deduplicate on the event id, which is stable across retries. A handler that double-credits an account on a retry is a defect in that handler, not in delivery.

Endpoint URLs are validated, and addresses on private or internal networks are refused. [The webhooks guide](https://developer.paygatehq.com/docs/webhooks) has verification code in three languages.

## 18. Rate limits and acceptable use\[technical account\]

Requests are rate-limited per principal across several independent budgets. Exceeding one returns `429` with a `Retry-After` header, which you should honour. Authentication endpoints have a much lower budget than the rest of the API.

You must not attempt to circumvent a limit, and you must not use the service in any way that degrades it for other merchants. What you may and may not take payment for is set out in §31.

## 19. Your customers’ data\[technical account\]

You may send us information about your own customers — a reference, an email address, a name, and arbitrary metadata of your choosing. As between us, **you are the controller of that information**. You warrant that you have a lawful basis for providing it and that doing so does not breach any obligation you owe your customer.

Do not put anything in a metadata field you would not want retained: the metadata is stored as you send it, and §22 governs how long.

The support contact a payer sees on a hosted checkout page is **yours**, not ours. Your customers’ support requests come to you.

## 20. Identity verification\[technical account\]

Identity verification is disabled by default and may be required before live mode is enabled for your account. Where it is enabled, the following applies.

Verification covers an individual, a business, or a representative of a business. Identity documents are captured in a flow that runs from your browser directly to the verification provider: **we never receive your documents.** The default configuration is manual review by our operators; where an automated provider is enabled, it is Didit, acting as our processor.

Of what the provider returns, the verified name, document number, date of birth and address are stored under envelope encryption. Only the document type, its country, its expiry date and its last four characters are held in the clear. Decrypting any sealed field passes through a single code path and writes an audit record of who read it and when.

A completed verification is valid for two years. A sanctions or adverse-media hit never results in automatic approval, and no operator can approve a case over a provider rejection or over such a hit.

Your responsibility, not ours

Verification may involve biometric processing of a face. Obtaining and recording your own consent — and, where you are verifying a representative of your business, theirs — is **your** obligation. Submitting a verification is your confirmation that you have done so.

## 21. What is not screened\[technical account\]

So that you do not assume a control that does not exist: **payer and wallet screening is not implemented. The blockchain addresses that funds arrive from are not checked against any sanctions list, any risk-scoring service, or anything else.**

Your obligations in respect of your own customers and the origin of their funds remain entirely yours. Nothing in the service discharges them, and the presence of merchant verification under §20 should not be read as implying any screening of the money itself.

## 22. Records, retention and deletion\[technical account\]

We state what the system actually does rather than what a policy would like it to.

**There is no erasure, anonymisation or bulk-export mechanism in the service.** Automatic expiry applies only to operational records: exchange-rate quotes, stored idempotency keys, expired sessions and tokens, rate-limit counters, and transaction cost observations. Everything else is retained until deliberately removed.

**Ledger entries and administrative audit records are append-only, enforced by the database itself. They cannot be edited or deleted — including at your request, and including at ours.** This is deliberate: the ledger is the only record of who is owed what, and an audit log that can be edited is not an audit log. Where a deletion request reaches records of this kind, we will tell you it cannot be performed rather than accept it and fail.

A privacy policy (§30) will describe retention for personal data specifically. It will inherit this constraint, because the constraint is in the database.

## 23. Availability, suspension and termination\[technical account\]

**These terms commit to no level of availability.** See §3. Our own dependencies — blockchain RPC providers above all — degrade, and when they degrade we degrade with them.

That is a property of _these_ terms, which are the standard ones. An enterprise agreement is negotiated separately and can carry a service level, along with settlement and support arrangements this document does not offer. Ask at support@paygatehq.com.

We may suspend or terminate an account for breach of these terms or where required by law. We will notify the contact address on the account, other than where the law prevents us. You may stop using the service at any time.

On termination, funds already held under §7 run to their release or their return under §9; nothing here strands money in the contract. Your obligations to your own customers survive termination, and are unaffected by it.

## 24. Disclaimers\[counsel-approved\]

The service is provided **“as is” and “as available”**. To the fullest extent permitted by law, paygate disclaims all warranties, express or implied, including merchantability, fitness for a particular purpose, non-infringement, and any warranty of uninterrupted or error-free operation.

We specifically make no warranty that:

-   the escrow contract is free of defects — an independent review found nine, all of which are fixed in what is deployed, and no review proves the absence of others; it is the contract every payment settles through;
-   any blockchain, node, RPC provider or third-party service will behave as expected, remain available, or remain economically usable;
-   a payment reported as paid will remain paid, or that a transfer sent in error can be recovered.

## 25. Limitation of liability\[counsel-approved\]

To the fullest extent permitted by law, paygate is not liable for indirect, incidental, special, consequential or exemplary damages, nor for lost profits, lost revenue or lost data, however caused.

Without limiting the above, we are **not** liable for loss arising from:

-   a blockchain reorganisation reversing a payment (§10);
-   funds sent on the wrong chain or to the wrong address (§11);
-   failure, degradation or error of any RPC provider or blockchain network;
-   compromise, loss or misuse of your API keys or account credentials (§14);
-   a payer revoking or under-funding a mandate (§12);
-   your use of the service in live mode notwithstanding §3.

Our aggregate liability arising out of or relating to the service is limited to the fees you paid us in the three months preceding the event giving rise to the claim. Where no fees were paid, our aggregate liability is limited to the maximum extent permitted by law.

## 26. Indemnity\[technical account\]

You will indemnify and hold harmless paygate against claims, losses and costs arising from the goods or services you sell, from the customer information you provide to us, from your breach of these terms or of applicable law, and from your use of the API.

## 27. Changes to these terms\[technical account\]

We may change these terms. Where a change is material we will notify the contact address on your account before it takes effect, and the effective date at the top of this document will change. Continuing to use the service after that date is acceptance. If you do not accept a change, stop using the service.

## 28. Governing law and disputes\[counsel-directed\]

**These terms do not choose a governing law or an exclusive forum.** paygate is not established in a jurisdiction chosen for that purpose, so there is none to name, and naming one we have no connection to would not make it true. The law that applies is whatever law applies to you where you are — including every mandatory protection you have there, which no term in this document can remove.

This will change when the service moves under a registered entity, and the change will be material: a governing law and a forum will be named, notified under §27, and you will be asked to accept the new version rather than being moved onto it.

## 29. Contact\[counsel-directed\]

Notices to us, and any other correspondence, go to support@paygatehq.com. There is no postal address to give: see §1.

For completeness, and consistent with §3: at the time of writing there is no staffed support channel. The only support address the product itself surfaces is **yours**, shown to your payers on the hosted checkout page.

## 30. Privacy\[technical account\]

Personal data is governed by our [privacy policy](/privacy), which forms part of these terms. It describes what is collected, who else processes it, and how long it is kept.

§22 constrains what that policy is able to offer, and it says so: ledger and audit records are append-only in the database and cannot be deleted on request, by you or by us.

## 31. Acceptable use\[technical account\]

You warrant that you will not use the service:

-   to obtain money by deception — including taking payment for goods or services you do not intend to supply, misrepresenting what a payment is for, or running any arrangement that pays earlier participants out of the money of later ones;
-   to sell, or to take payment for, anything you may not lawfully sell — in your jurisdiction or in your customer’s;
-   to launder the proceeds of crime, to disguise where funds came from or where they are going, or to transact with a person or country you are prohibited from transacting with;
-   to accept payments that belong to somebody else as though they were your own, or otherwise to run a money transmission, exchange or remittance business through your account;
-   to charge a subscription or a mandate on terms you have not disclosed to the payer (§12).

**None of this is screened for.** As §21 sets out, we do not check payers, wallet addresses or the origin of funds against anything. The list above is a promise you make to us, not a control we operate — and the responsibility for what you sell, to whom, and whether it is lawful for you to do so, is yours alone (§4).

**What we can do if you break it.** Two things, and they are the only two. We can suspend your account under §23, which ends your sessions and refuses your API keys immediately. And we can refuse to verify the identity documents behind the account — on it and on any account opened later with the same document, because that refusal attaches to the document rather than to the email address. Either may be permanent.

**What we cannot do, whatever you have done.** We never hold your money (§6, §7). The escrow contract has exactly two exits and neither of them takes a destination: a hold is released to your registered payout address or returned to the payer who funded it, and there is no third option for anybody, including us. So we cannot freeze funds, reverse a settled payment, or move money to ourselves or to anyone else. Suspending an account does not touch anything already on chain — holds run to their release or their return under §9 exactly as they would have.

This has a consequence for anyone who has paid a merchant we later suspend: **we are not able to recover your money**, and your claim is against the merchant, not against us. Suspension stops an account being used again. It is not a remedy, and §24 and §25 are not narrowed by this section.

To report a merchant using the service for any of the above, write to support@paygatehq.com.

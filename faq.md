---
title: "USDT payment gateway FAQ — straight answers | paygate"
description: "How USDT payments work for a business: do you need a developer, where the money goes, chargebacks, refunds, fees, and how fast you get paid."
source: "https://paygatehq.com/faq"
---

Frequently asked

# Questions about accepting USDT

What it costs, where the money goes, what happens when something goes wrong, and what we cannot do. Written for a business owner rather than a developer.

## Contents

-   [What is paygate?](#what-is-paygate)
-   [Do I need a developer to use paygate?](#do-i-need-a-developer)
-   [How do my customers pay?](#how-do-customers-pay)
-   [Which cryptocurrencies can I accept?](#what-crypto-can-i-accept)
-   [Do I need to understand crypto or hold a wallet?](#do-i-need-to-understand-crypto)
-   [Where does the money go? Do you hold my funds?](#where-does-the-money-go)
-   [Can a customer charge back a USDT payment?](#chargebacks)
-   [How fast do I get paid?](#how-fast-do-i-get-paid)
-   [Can I refund a customer?](#refunds)
-   [Can I convert USDT to my local currency?](#convert-to-local-currency)
-   [How much does paygate cost?](#what-does-it-cost)
-   [Is accepting USDT cheaper than accepting cards?](#cheaper-than-cards)
-   [Can I bill customers monthly with crypto?](#subscriptions)
-   [What happens if a customer pays the wrong amount?](#underpaid-overpaid)
-   [What if a customer sends on the wrong network?](#wrong-network)
-   [Which countries can use paygate?](#which-countries)
-   [Is paygate live? Can I take real payments today?](#is-it-live)
-   [How do I know my money is safe?](#is-it-safe)

## Getting started

### What is paygate?

paygate is a payment gateway that lets a business accept USDT (Tether) from its customers and receive the money directly into its own crypto wallet.

You create a payment in the dashboard or through the API, send your customer the link, and they pay from a hosted checkout page. paygate watches the blockchain, matches the incoming transfer to your payment, and tells you it arrived.

It supports one-off payments, invoices and recurring subscriptions. Payments and invoices work on both the Tron and BNB Smart Chain networks; recurring subscriptions run on BNB Smart Chain.

### Do I need a developer to use paygate?

No. You can create a payment in the paygate dashboard, copy the checkout link, and send it to your customer by email, WhatsApp or any other channel — no code at all.

A developer is only needed if you want payments created automatically by your own website or app, which is what the API and webhooks are for.

### How do my customers pay?

Your customer opens the checkout link and sees a QR code, the exact amount to send, and a countdown — they pay from any crypto wallet or exchange account.

The page updates itself the moment the transfer is confirmed on the blockchain, so neither of you has to refresh or wonder whether it went through. Customers with a browser wallet such as MetaMask or TronLink can pay in one click instead of scanning.

Your business name, logo and support address appear on the page, so it looks like yours rather than ours.

### Which cryptocurrencies can I accept?

paygate supports USDT (Tether) on two networks: Tron (TRC20) and BNB Smart Chain (BEP20).

USDT is a stablecoin pegged to the US dollar, which is the point — your customer pays and you receive an amount that does not move overnight the way Bitcoin does. Other coins and networks are not supported.

### Do I need to understand crypto or hold a wallet?

You need one crypto wallet address to receive money into, and paygate can generate one for you in your browser during setup.

Beyond that, no. You never handle private keys through us, never install a wallet library, and never touch a blockchain node. The dashboard shows amounts in plain figures and your own currency alongside USDT.

## Your money

### Where does the money go? Do you hold my funds?

Your customer pays a deposit address belonging to that one payment. The money is swept into our escrow contract, held for your 7 days refund window, and then released to the payout wallet you registered.

It never reaches an account of ours, and that is a property of the contract rather than a policy we keep. There are exactly two ways out of it — release to your payout address, and refund to the payer who sent it — and neither takes a destination as a parameter. There is no address either function could be pointed at, by anyone, including us.

What the hold buys you is the refund window. Money already in your wallet can only be given back by you sending it; money on the contract can be returned to your customer from your dashboard while the window is open.

### Can a customer charge back a USDT payment?

No. A blockchain transfer cannot be reversed by the sender, their bank, or a card network, so there is no chargeback process and no chargeback fees.

This is the main reason merchants selling digital goods, services or cross-border move to stablecoin payments — card chargeback rates and the fees attached to them disappear entirely.

It cuts both ways, and we would rather say so: if you want to refund a customer as a goodwill gesture, that is something you choose to do, not something a network forces on you.

### How fast do I get paid?

The payment is confirmed and irreversible within minutes, and it reaches your own wallet 7 days later. Those are two different moments and the gap between them is deliberate.

What happens in between is the refund window: your customer's money sits in the escrow contract, where you can return it to them and nobody else can move it — not us, not them, not a bank. After 7 days it is released to the wallet you registered, minus the fee.

There is no weekend delay and no rolling reserve held back against future disputes. A card payment also takes days to arrive, and then stays reversible for months afterwards; this one is final from the moment it confirms.

### Can I refund a customer?

Yes, and you are the one who does it: while the payment is still inside its 7 days hold window you can return part or all of it to the payer from your dashboard, and it goes back to the address it came from.

paygate cannot do it for you and cannot do it to you. The contract accepts a return only from the wallet you registered, never from us — so a payer who wants money back asks you, the same as anywhere else.

Once the window closes the money is in your own wallet and the contract has nothing left to return. After that a refund is an ordinary transfer you send yourself.

### Can I convert USDT to my local currency?

Not through paygate — we deliver USDT to your wallet, and converting it to local currency is something you do at an exchange or with a broker you already use.

We can price in your local currency, so your customer sees a figure they recognise and pays the USDT equivalent at the current rate. But the money that arrives is USDT.

## Cost

### How much does paygate cost?

Every payment is charged a flat 2%, the same rate at every size, with no monthly fee, setup fee or minimum.

Blockchain network fees are separate and are not ours — they go to the network and are typically a few cents. Merchants doing high volume can ask about Enterprise pricing.

### Is accepting USDT cheaper than accepting cards?

Usually, yes — card processing typically costs around 2.9% plus a fixed fee per transaction, plus chargeback fees, currency conversion margins and monthly gateway charges that stablecoin payments do not have.

The gap widens on cross-border sales, where card networks add foreign transaction costs and banks add a conversion spread. It widens again on small payments, where a fixed per-transaction fee is a large share of the total.

## Day to day

### Can I bill customers monthly with crypto?

Yes. Your customer approves a spending limit once, and you can charge up to that limit each billing period without asking them again.

A blockchain has no direct debit, so this works differently from a card on file: the permission lives on the blockchain, your customer sets the ceiling, and they can cancel it themselves at any time without going through you or us. Trials, usage-based billing, discount codes and failed-payment retries are all supported on top of it.

Subscriptions run on BNB Smart Chain. Every charge is a transaction on the network, and on BNB Smart Chain that costs a fraction of a cent — on Tron the same charge costs dollars, which no sensible subscription price can carry. One-off payments and invoices work on Tron exactly as before.

### What happens if a customer pays the wrong amount?

The payment is marked underpaid or overpaid rather than simply failing, and you decide what to do about it.

Customers regularly send slightly too little because their wallet deducted a fee, or too much because they rounded up. paygate records exactly what arrived, lets the customer top up a short payment, and shows you the difference instead of leaving you to reconcile it by hand.

### What if a customer sends on the wrong network?

Funds sent on the wrong blockchain network are usually unrecoverable, by us or by anyone — this is true of every crypto payment processor, not just paygate.

The checkout page states the network prominently and generates a QR code that carries it, which prevents most of these. We would rather tell you this up front than have you discover it from a customer.

### Which countries can use paygate?

paygate is not restricted to a particular country, but you are responsible for checking that accepting cryptocurrency is lawful for your business where you operate.

Rules differ sharply between jurisdictions and change often. We do not give legal advice and nothing in the product should be read as confirmation that crypto payments are permitted for you.

## Straight answers

### Is paygate live? Can I take real payments today?

Yes. You can open an account, take test payments while you build, and switch the same integration to live money when you are ready — the API and the checkout are identical in both modes.

What you should know before you build on us: we are new, we settle in USDT rather than your own currency, and we do not stand between you and your customer in a dispute. All of that is on this page rather than buried, because you would find it out anyway and it is better found now.

### How do I know my money is safe?

Your money never passes through an account of ours, so there is no paygate balance for us to lose or freeze. It rests in the escrow contract for the refund window and is then released to the wallet you registered.

Two things about that contract are worth knowing and are in our terms in plain words. It was independently audited in September 2026 — nine findings, three of them high severity, all fixed. And we cannot move what it holds: the only two ways out are release to your payout address and refund to the payer who sent it, neither of which lets anyone name a destination — including us.

## Still deciding?

Open an account and take a test payment — it costs nothing and takes a few minutes.

[Create a payment link — free](https://app.paygatehq.com)[See pricing](/pricing)

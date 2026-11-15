# Awesome-Online-Payment-Pages-Checkout

# Awesome Online Payment Pages & Checkout

> A curated list of top Online Payment Page and Checkout platforms — both SaaS/Hosted commercial solutions and open-source alternatives for accepting payments with hosted, embeddable, or self-hosted checkout experiences.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Stripe Checkout](#stripe-checkout)
  - [PayPal Commerce Platform](#paypal-commerce-platform)
  - [Square Online Checkout](#square-online-checkout)
  - [Adyen](#adyen)
  - [Braintree](#braintree)
  - [Mollie](#mollie)
- [Open-Source Software](#-open-source-software)
  - [Open Payment Host](#open-payment-host)
  - [Zoneless](#zoneless)
  - [TPT Pay](#tpt-pay)
  - [Spree Commerce Storefront](#spree-commerce-storefront)
  - [StatiCart](#staticart)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Online Payment Page and Checkout platforms. These are not open-source but are included as reference points for feature comparison.

### Stripe Checkout
**Type:** Hosted checkout sessions with Stripe's payment infrastructure
Stripe Checkout provides hosted payment pages for one-time payments and subscriptions, with built-in support for cards, digital wallets, bank redirects, and local payment methods. It handles PCI compliance, 3D Secure, and tax calculation, and is the benchmark against which open-source alternatives like Zoneless and TPT Pay are measured.

### PayPal Commerce Platform
**Type:** Hosted checkout with broad consumer reach
PayPal's Commerce Platform provides hosted checkout accepting PayPal, Venmo, Pay Later, and major cards across 200+ markets. It manages PCI compliance for the hosted flow and includes built-in risk management and Seller Protection.

### Square Online Checkout
**Type:** Hosted payment links and checkout
Square provides hosted checkout through payment links and integrations, redirecting buyers to a Square-hosted page to complete payment. It supports pre-populated buyer information and automated payment reminders.

### Adyen
**Type:** Enterprise hosted checkout with theme customization
Adyen's Hosted Checkout supports theme creation with brand logo, display name, and default settings, with the theme ID passed in the session request. It supports a wide range of payment methods filtered by shopper country and currency.

### Braintree
**Type:** PayPal-owned gateway with Drop-in UI
Braintree provides card and digital wallet processing with its Drop-in UI, which simplifies PCI compliance by handling card data collection. It is often chosen by businesses already in the PayPal ecosystem.

### Mollie
**Type:** European payment links and hosted checkout
Mollie provides Payment Links that direct customers to a branded checkout page from any channel, with support for local European payment methods. It handles the payment page and PCI compliance for the hosted flow.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Online Payment Page and Checkout tools. The open-source ecosystem spans **self-hosted payment hosts**, **Stripe-compatible alternatives**, **self-hostable payment APIs**, and **storefronts with checkout**.

### Open Payment Host
**Stack:** Go / PostgreSQL or SQLite | **License:** Open Source (MIT-style) 
Open Payment Host is a self-hosted payment service for selling digital or physical goods without marketplace commissions, positioned as an alternative to Gumroad, Buy Me a Coffee, and Ko-fi [citation:1][citation:3]. Key features include:
- **Hosted checkout and billing endpoints** with REST API calls like `/checkout/create` and `/subscription/create`
- **Webhook handling** for payment success, refunds, and subscription changes, with at-least-once delivery and ordered events per product [citation:3]
- **Multi-PSP support** including Stripe, Square, Razorpay, and PayPal
- **Subscription cancellation** with single-use tokens and CSRF protection [citation:3]
- **Docker Compose and Go build** deployment options

The project has 243 stars and was last updated in September 2026 [citation:1]. It is positioned for teams wanting full control over their payment flow without marketplace fees.
**Best for:** Businesses wanting a self-hosted payment host with subscription support and multi-provider webhooks, accepting the Go/PostgreSQL stack and moderate production readiness [citation:1].

### Zoneless
**Stack:** TypeScript / MongoDB / Express / Angular | **License:** Apache-2.0 
Zoneless is an open-source **Stripe alternative for stablecoins**, providing checkout, subscriptions, and marketplace payouts through a **Stripe-compatible API** [citation:2]. Key features include:
- **Hosted checkout** for USDC payments with products and payment links
- **Subscriptions** with recurring payments, invoices, and status management
- **Marketplace seller onboarding** with identity verification and Express-style dashboards
- **Stripe-compatible object shapes** (Checkout Sessions, Payment Links, Customers, Subscriptions) and webhook patterns

It was built for PromptBase (500,000+ users) and runs its seller payout infrastructure in production [citation:2]. Deployment via `docker compose up` with MongoDB.
**Best for:** Marketplaces and businesses wanting a Stripe-compatible checkout API for stablecoin payments, particularly those in the crypto/USDC ecosystem.

### TPT Pay
**Stack:** Go / PostgreSQL / NATS / Vault | **License:** MIT 
TPT Pay is a self-hostable **open-source Stripe alternative** with a REST API compatible with **Stripe API v2024-06-20**, an append-only double-entry ledger, and a `CardNetworkAdapter` interface that abstracts card network access [citation:7]. Key characteristics:
- **SandboxAdapter** ships for testing, with `BankSponsorAdapter` or `DirectAcquiringAdapter` planned for production
- **Webhook engine** via NATS JetStream for delivery and async jobs
- **HashiCorp Vault** for card tokenization and API key encryption
- **Merchant dashboard** (Next.js) and JavaScript/Python SDKs in development

**Important:** The card network adapter is not yet production-ready—you must plug in a real adapter for live card processing [citation:7]. The project is MIT licensed and free to deploy.
**Best for:** Developers wanting an MIT-licensed, Stripe-API-compatible payment API with a double-entry ledger, accepting that card network connectivity is not yet available out of the box.

### Spree Commerce Storefront
**Stack:** Next.js / TypeScript / React | **License:** MIT (storefront) 
Spree's Next.js Storefront is a production-ready, headless ecommerce storefront with **one-page checkout** supporting guest and authenticated users, multi-shipment, coupons, gift cards, and store credit [citation:11]. Key checkout features include:
- **Native Stripe, Adyen, and PayPal payments** via Payment Sessions, with card data never touching your server
- **3D Secure** and support for Apple Pay, Google Pay, Klarna, Affirm, and SEPA
- **Multi-region support** with country, currency, and language switching
- **Wholesale portal** for B2B pricing and product gating
- **Lighthouse scores** of 98/100 desktop and 88/100 mobile [citation:11]

It is MIT licensed and built on Next.js 16 and React 19. The storefront is the frontend layer—the Spree Commerce backend is a separate Ruby on Rails application.
**Best for:** Teams wanting a modern, production-ready storefront with checkout built in, accepting the Next.js/Spree backend stack.

### StatiCart
**Stack:** JavaScript / Stripe / DynamoDB / Lambda | **License:** Open Source 
StatiCart is a free, open-source, Stripe-powered ecommerce platform with a **static site + thin API** architecture [citation:8]. Key characteristics:
- **Static site on CDN** for product pages and cart (localStorage)
- **Thin Lambda API** for checkout, webhooks, stock, and orders
- **DynamoDB single-table** database
- **Config-driven branding** via `staticart.config.json`
- **Platform stacking** via Clearstack for component overrides

It is positioned as a cheaply hosted, limited-scope ecommerce solution for developers wanting Stripe checkout without a full platform [citation:8].
**Best for:** Developers wanting a lightweight, Stripe-powered checkout with static hosting and minimal infrastructure, accepting a limited-scope ecommerce feature set.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Hosted Checkout | Subscription Support | Self-Hosted | Best For |
|----------|---------|-------|-----------------|----------------------|-------------|----------|
| **Stripe Checkout** | Proprietary | Cloud | ✅ | ✅ | ❌ | Standard hosted checkout |
| **PayPal Commerce** | Proprietary | Cloud | ✅ | ✅ | ❌ | Broad consumer reach |
| **Open Payment Host** | Open Source | Go/Postgres | ✅ | ✅ | ✅ | Self-hosted checkout + webhooks |
| **Zoneless** | Apache-2.0 | TypeScript/MongoDB | ✅ | ✅ | ✅ | Stablecoin Stripe alternative |
| **TPT Pay** | MIT | Go/Postgres | (API) | (Check) | ✅ | Stripe-compatible API + ledger |
| **Spree Storefront** | MIT | Next.js | ✅ One-page | (Spree backend) | ✅ | Production storefront + checkout |
| **StatiCart** | Open Source | JS/Stripe/DynamoDB | ✅ Stripe | (Check) | ✅ | Lightweight static store |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Online Payment Page or Checkout tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** Open-source checkout splits between **self-hosted payment hosts** (Open Payment Host with multi-PSP webhooks, Zoneless for stablecoins, TPT Pay with a Stripe-compatible API) and **storefronts with checkout** (Spree Storefront, StatiCart). **Open Payment Host** is the most mature self-hosted option for traditional card payments with subscription support [citation:1][citation:3], while **Zoneless** offers the strongest Stripe API compatibility for crypto-native businesses [citation:2]. **TPT Pay** provides a promising MIT-licensed foundation but requires a production card adapter [citation:7]. No open-source project fully replicates Stripe Checkout's breadth of payment methods and fraud tooling—for production card acquiring, commercial gateways remain the practical choice.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐

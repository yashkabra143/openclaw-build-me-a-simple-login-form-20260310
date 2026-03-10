# SEO & Performance Report

**Project:** build me a simple login form
**Date:** 2026-03-10
**Agent:** seo-optimizer

---

# Complete SEO & Performance Plan
## User Authentication Login Form — Version 1.0

---

## ⚠️ Strategic Context Note

> A **login page** is a transactional/functional page, not a content-discovery page. The SEO strategy here is **two-tiered**: (1) minimize indexing friction on the login page itself, and (2) build SEO authority around the *product* that the login page gates. Both tiers are covered below.

---

## 1. Meta Tags

### 1.1 Login Page Meta Tags

```html
<!-- Primary Meta Tags -->
<title>Sign In | [Product Name] — Secure Access to Your Account</title>
<meta name="description"
      content="Sign in to [Product Name] to access your dashboard,
               manage settings, and continue where you left off.
               Your account is protected with enterprise-grade security." />
<meta name="robots" content="noindex, nofollow" />
<!--
  ^^^  CRITICAL DECISION: Login pages should NOT be indexed.
       Reasons:
       - Duplicate thin content risk
       - No organic search intent matches "login to [your-app]"
       - Prevents crawl budget waste
       - Reduces attack-surface visibility
-->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<meta charset="UTF-8" />
<link rel="canonical" href="https://app.yourdomain.com/login" />

<!-- Open Graph (for shared links in Slack, email previews, etc.) -->
<meta property="og:type"        content="website" />
<meta property="og:title"       content="Sign In | [Product Name]" />
<meta property="og:description" content="Access your [Product Name] account securely." />
<meta property="og:url"         content="https://app.yourdomain.com/login" />
<meta property="og:image"       content="https://cdn.yourdomain.com/og/login-preview.png" />
<meta property="og:image:width"  content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:site_name"   content="[Product Name]" />

<!-- Twitter Card -->
<meta name="twitter:card"        content="summary_large_image" />
<meta name="twitter:title"       content="Sign In | [Product Name]" />
<meta name="twitter:description" content="Access your [Product Name] account securely." />
<meta name="twitter:image"       content="https://cdn.yourdomain.com/og/login-preview.png" />
<meta name="twitter:site"        content="@YourHandle" />

<!-- Security Headers (via HTTP, not meta — listed here for completeness) -->
<!--
  Content-Security-Policy: default-src 'self'; script-src 'self' 'nonce-{SERVER_NONCE}'
  Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin
-->
```

### 1.2 Marketing/Landing Page Meta Tags (Indexable — drives discovery)

```html
<!-- This is the page that SHOULD rank, not /login -->
<title>[Product Name] — [Core Value Prop in 6 Words] | Free Trial</title>
<meta name="description"
      content="[Product Name] helps [target persona] to [primary benefit]
               in [timeframe]. Trusted by [X]+ teams. Start free today." />
<meta name="robots" content="index, follow, max-snippet:-1,
                              max-image-preview:large,
                              max-video-preview:-1" />

<!-- Open Graph — Marketing Page -->
<meta property="og:type"        content="website" />
<meta property="og:title"       content="[Product Name] — [Value Prop]" />
<meta property="og:description" content="[Benefit-driven 2-sentence description]" />
<meta property="og:url"         content="https://www.yourdomain.com/" />
<meta property="og:image"       content="https://cdn.yourdomain.com/og/homepage.png" />
```

---

## 2. Structured Data (JSON-LD)

### 2.1 Organization Schema (Global — all pages)

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://www.yourdomain.com/#organization",
  "name": "[Product Name]",
  "url": "https://www.yourdomain.com",
  "logo": {
    "@type": "ImageObject",
    "url": "https://cdn.yourdomain.com/brand/logo-512x512.png",
    "width": 512,
    "height": 512
  },
  "sameAs": [
    "https://twitter.com/YourHandle",
    "https://linkedin.com/company/your-company",
    "https://github.com/your-org"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "contactType": "customer support",
    "email": "support@yourdomain.com",
    "availableLanguage": ["English"]
  }
}
```

### 2.2 WebApplication Schema (Product pages)

```json
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "@id": "https://www.yourdomain.com/#webapp",
  "name": "[Product Name]",
  "url": "https://www.yourdomain.com",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web Browser",
  "description": "[Clear product description under 160 chars]",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "USD",
    "description": "Free trial available"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "247",
    "bestRating": "5"
  },
  "featureList": [
    "Secure user authentication",
    "Multi-factor authentication",
    "Single Sign-On (SSO)",
    "Role-based access control"
  ]
}
```

### 2.3 BreadcrumbList Schema (Login page)

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://www.yourdomain.com"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Sign In",
      "item": "https://app.yourdomain.com/login"
    }
  ]
}
```

### 2.4 SiteLinksSearchBox Schema (Homepage)

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://www.yourdomain.com/#website",
  "url": "https://www.yourdomain.com",
  "name": "[Product Name]",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://www.yourdomain.com/search?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```

### 2.5 FAQ Schema (Help/Support pages around authentication)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How do I reset my [Product Name] password?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Click 'Forgot Password' on the login page, enter your email address,
                 and follow the reset link sent to your inbox. Links expire in 24 hours."
      }
    },
    {
      "@type": "Question",
      "name": "Does [Product Name] support two-factor authentication?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. [Product Name] supports TOTP-based 2FA via authenticator apps
                 (Google Authenticator, Authy) and SMS verification."
      }
    },
    {
      "@type": "Question",
      "name": "What should I do if I'm locked out of my account?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "After 5 failed attempts, accounts are temporarily locked for security.
                 Contact support@yourdomain.com or wait 30 minutes for automatic unlock."
      }
    }
  ]
}
```

---

## 3. Technical SEO

### 3.1 Sitemap Strategy

```xml
<!-- /sitemap_index.xml — Sitemap Index File -->
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

  <!-- Marketing site sitemap -->
  <sitemap>
    <loc>https://www.yourdomain.com/sitemap-marketing.xml</loc>
    <lastmod>2025-01-15</lastmod>
  </sitemap>

  <!-- Blog/content sitemap -->
  <sitemap>
    <loc>https://www.yourdomain.com/sitemap-blog.xml</loc>
    <lastmod>2025-01-15</lastmod>
  </sitemap>

  <!-- Help center sitemap -->
  <sitemap>
    <loc>https://help.yourdomain.com/sitemap-help.xml</loc>
    <lastmod>2025-01-15</lastmod>
  </sitemap>

  <!--
    NOTE: /app sitemap intentionally EXCLUDED.
    Authenticated app pages (dashboard, settings, etc.)
    should never be in a public sitemap.
  -->

</sitemapindex>
```

```xml
<!-- /sitemap-marketing.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">

  <url>
    <loc>https://www.yourdomain.com/</loc>
    <lastmod>2025-01-15</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>

  <url>
    <loc>https://www.yourdomain.com/features</loc>
    <lastmod>2025-01-15</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.9</priority>
  </url>

  <url>
    <loc>https://www.yourdomain.com/pricing</loc>
    <lastmod>2025-01-15</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.9</priority>
  </url>

  <url>
    <loc>https://www.yourdomain.com/security</loc>
    <lastmod>2025-01-15</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>

  <!--
    LOGIN PAGE INTENTIONALLY EXCLUDED from sitemap.
    It carries noindex, so including it wastes crawl budget.
  -->

</urlset>
```

### 3.2 robots.txt

```txt
# robots.txt —
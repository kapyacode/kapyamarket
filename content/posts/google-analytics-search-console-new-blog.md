---
title: "How to Set Up Google Analytics and Search Console on a New Blog"
date: 2026-11-15T17:00:00+02:00
draft: false
slug: "google-analytics-search-console-new-blog"
url: "/2026/11/google-analytics-search-console-new-blog/"
description: "A step-by-step beginner guide to setting up Google Analytics 4 and Google Search Console on a new blog: create the accounts, add the tracking code, submit your sitemap and check your data."
tags:
  - "Google Analytics"
  - "Search Console"
  - "Blogging Tips"
  - "Website Guides"
cover:
  image: "/images/ga-search-console-guide.png"
  alt: "How to set up Google Analytics and Search Console on a new blog"
  hiddenInSingle: true
---

Once you start publishing, two free Google tools tell you what happens next. **Google Analytics** shows what visitors do on your blog, and **Google Search Console** shows how your blog appears in Google Search. Set up both early, so the data starts building from your first post.

![How to set up Google Analytics and Search Console on a new blog](/images/ga-search-console-guide.png)

*Illustration: the numbers in this picture are examples, not real results.*

## What each tool does

- **Google Analytics** shows how many people visit, where they come from and which pages they read.
- **Google Search Console** shows which searches bring your site up, how often people click, and whether Google has any problems reading your pages.

They answer different questions, so you want both.

## Step 1: Create a Google account

If you do not have one, create it at accounts.google.com. Use an account you will keep for the long term, and use the same one for both tools. That makes it easy to link them later.

## Step 2: Set up Google Analytics

1. Go to analytics.google.com and sign in.
2. Click **Start measuring** (or **Admin**, then **Create**, then **Account**) and give the account your blog's name.
3. Create a **property**. Choose a name, your time zone and your currency.
4. Answer the business questions. They only shape the reports you see.
5. Choose **Web** as the platform, enter your blog address (for example `https://www.yourblog.co.za`) and a stream name.
6. Copy the **Measurement ID**. It starts with `G-`.

### Add the code to your blog

- **Blogger:** open **Settings** and look for the Google Analytics field, then paste your Measurement ID. If your version of Blogger does not accept it, add the code below to your theme instead.
- **WordPress:** use a plugin such as Site Kit by Google, or the header setting in your theme.
- **Any other site:** paste this code just before the closing `</head>` tag:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

Replace both `G-XXXXXXXXXX` with your own ID. Add it only once. If a plugin and your theme both add it, every visit is counted twice.

### Check that it works

Open **Reports**, then **Realtime**. On your phone, using mobile data, open your blog. Within a minute or two you should see one user. Your own computer may hide your visit if you use an ad blocker.

The warning "No data received" on the data stream page can take up to 48 hours to disappear, even when Realtime already works.

Analytics uses cookies, so mention it in your privacy and cookie policy. If you have readers in the EU or the UK, add a consent message as well. Our own [Cookie Policy](/p/cookie-policy/) shows one way to describe it.

## Step 3: Set up Google Search Console

1. Go to search.google.com/search-console and sign in with the same Google account.
2. Click **Add property**. There are two types:
   - **Domain** covers every version of your address, and needs a DNS record at your domain provider.
   - **URL prefix** covers one exact address and offers more ways to verify. Beginners usually choose this one, and type the address exactly as it appears in the browser, including `https` and `www` if you use it.
3. **Verify ownership.** Follow the screen. The options include an HTML tag, a DNS record and your Analytics tag if it is already on the site. Click **Verify**. Keep the verification in place for good, because removing it can make you lose access.
4. **Submit your sitemap.** Open **Sitemaps** in the left menu and type the address of your sitemap file. On Blogger and many site generators it is `sitemap.xml`. Some WordPress SEO plugins use `sitemap_index.xml`. The status should change to **Success**.
5. **Ask Google to look at a new post.** Paste its address into the search bar at the top and click **Request indexing**. It speeds things up a little, but it is not instant.

## Step 4: Check your data

**In Google Analytics**

- **Realtime** shows who is on your blog now.
- **Reports**, then **Acquisition**, shows where visitors come from.
- **Reports**, then **Engagement**, then **Pages and screens**, shows which posts get read.

Standard reports can take 24 to 48 hours to fill in.

**In Search Console**

- **Performance** shows clicks, impressions, the click rate and your average position in search results.
- **Pages** (under Indexing) shows which pages Google has added, and why others are not included yet.

A new blog often shows very little at first. It can take days or weeks before a new site appears in search results, so do not worry if the first reports look empty.

## Link the two tools (optional)

In Analytics, open **Admin**, then **Product links**, then **Search Console links**, and click **Link**. Your search data then appears inside your Analytics reports. You need access to both accounts.

## Common problems

- **No data in Analytics after a day:** the ID may be wrong, or the code is not in the `<head>` of your pages. Open your blog, view the page source and search for your `G-` ID.
- **Every visit counted twice:** the code was added twice, for example by a plugin and by your theme.
- **Search Console cannot verify you:** DNS changes can take a while, so wait and try again. Also check that you typed the exact address, with or without `www`.
- **The sitemap "could not be fetched":** open the sitemap address in your browser first. If it loads, wait a while and submit it again.
- **A page is "not indexed":** this is normal for new pages. Request indexing, and make sure the page is not blocked.

## What to do next

Look at your data once a week, not once an hour. See which posts get visitors and which searches bring them, and write more about those topics.

If you are moving a blog to a new platform, our guide on [how to move from Blogger to Hugo and Cloudflare](/2026/11/move-blogger-to-hugo-cloudflare-free/) explains how to keep your Search Console access and your post addresses. Questions about setting this up? Use the [contact page](/p/contact-us/).
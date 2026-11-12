---
title: "How to Connect a .co.za Domain to Blogger (Step by Step)"
date: 2026-11-06T13:01:38Z
slug: "how-to-connect-coza-domain-to-blogger"
url: "/2026/11/how-to-connect-coza-domain-to-blogger.html"
description: "Learn how to point your .co.za domain to Blogger using CNAME and A records. Simple steps for beginners, plus fixes for common errors."
cover:
  image: "/images/blog/db2bc43b8218.png"
  hiddenInSingle: true
---

<!-- ===== BLOGGER POST SETTINGS (set these in the right sidebar, not in the HTML) =====
Title: How to Connect a .co.za Domain to Blogger (Step by Step)
Permalink (custom): connect-coza-domain-to-blogger
Search description: Learn how to point your .co.za domain to Blogger using CNAME and A records. Simple steps for beginners, plus fixes for common errors.
Labels: Blogger, Domains, Website Guides
IMAGES: The 4 images are embedded inside this code, so no upload is needed.
If Blogger does not show them after you paste, use the upload method instead.
===== PASTE EVERYTHING BELOW THIS LINE INTO BLOGGER'S HTML VIEW ===== -->

<p><em>Affiliate Disclosure: This post contains affiliate links. If you buy through them, I may earn a commission at no extra cost to you. <a href="https://www.kapyamarket.co.za/p/affiliate-disclosure.html">Read my full Affiliate Disclosure</a> for more info.</em></p>

<p style="text-align: center;"><img alt="How to connect a .co.za domain to Blogger, step-by-step guide for beginners" height="630" src="/images/blog/db2bc43b8218.png" style="border-radius: 8px; height: auto; max-width: 100%;" width="1200" /></p>

<p>Blogger is free, but a yourname.blogspot.com address looks amateur and is hard to remember. A .co.za domain fixes that. Connecting the two takes about 15 minutes of work, plus some waiting time while the settings spread across the internet.</p>

<p>This guide shows you exactly what to click and what to type, even if you have never touched DNS settings before.</p>

<h2>What you need before you start</h2>
<ul>
  <li>A Blogger blog</li>
  <li>A domain you own</li>
  <li>Login details for the company where you registered the domain (your registrar)</li>
</ul>

<p><strong>Don’t have a domain yet?</strong> You can <a href="https://hostafrica.co.za/domains/tld/co-za?aff=3166" rel="sponsored noopener" target="_blank">register a .co.za domain with HostAfrica</a>, a South African company that bills in rands. If you want to compare options first, read my guide on <a href="https://www.kapyamarket.co.za/2026/11/how-to-register-coza-domain-in-south.html">how to register a .co.za domain</a>, including what it costs at renewal.</p>

<h2>How it works in plain language</h2>
<p>Your domain is like a street address. DNS records are the directions that tell the internet where that address leads, and your registrar stores them. You will add a few records that say: “When someone types my domain, send them to Blogger.”</p>

<p style="text-align: center;"><img alt="Diagram showing how a visitor reaches a Blogger blog through the registrar's DNS records" height="520" src="/images/blog/279d2389a171.png" style="border-radius: 8px; height: auto; max-width: 100%;" width="1200" /></p>

<h2>Step 1: Tell Blogger your domain</h2>
<ol>
  <li>Log in to Blogger and open your blog.</li>
  <li>Go to <strong>Settings</strong> and find the <strong>Publishing</strong> section.</li>
  <li>Choose <strong>Custom domain</strong>.</li>
  <li>Type your domain <strong>with www at the front</strong>, for example <code>www.yourdomain.co.za</code>.</li>
  <li>Click <strong>Save</strong>.</li>
</ol>
<p>Blogger will show an error. This is normal. It also shows you two CNAME records you need to create, so keep this page open or copy them down.</p>

<h2>Step 2: Add the two CNAME records</h2>
<p>Log in to your registrar and find the DNS settings, often called “DNS management” or “DNS zone”. Add these two records:</p>

<div style="overflow-x: auto;">
<table style="border-collapse: collapse; margin: 16px 0; width: 100%;">
  <thead>
    <tr>
      <th style="background: #f2f2f2; border: 1px solid #cccccc; padding: 8px; text-align: left;">Type</th>
      <th style="background: #f2f2f2; border: 1px solid #cccccc; padding: 8px; text-align: left;">Name</th>
      <th style="background: #f2f2f2; border: 1px solid #cccccc; padding: 8px; text-align: left;">Points to</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid #cccccc; padding: 8px;">CNAME</td>
      <td style="border: 1px solid #cccccc; padding: 8px;"><code>www</code></td>
      <td style="border: 1px solid #cccccc; padding: 8px;"><code>ghs.google.com</code></td>
    </tr>
    <tr>
      <td style="border: 1px solid #cccccc; padding: 8px;">CNAME</td>
      <td style="border: 1px solid #cccccc; padding: 8px;">the unique name Blogger showed you</td>
      <td style="border: 1px solid #cccccc; padding: 8px;">the unique destination Blogger showed you</td>
    </tr>
  </tbody>
</table>
</div>

<p>The first record is the same for everyone. The second is unique to your blog and Google account, so copy it exactly from your Blogger screen. Some registrars want a dot at the end of the destination. If one rejects your entry, try adding or removing the dot.</p>

<h2>Step 3: Add A records so the non-www version works</h2>
<p>Without this step, people who type <code>yourdomain.co.za</code> without the www may see an error. Add four A records for your root domain (the name is usually <code>@</code>), pointing to these Google addresses:</p>
<ul>
  <li><code>216.239.32.21</code></li>
  <li><code>216.239.34.21</code></li>
  <li><code>216.239.36.21</code></li>
  <li><code>216.239.38.21</code></li>
</ul>
<p>If your root domain already has other A records, delete them first so they don’t conflict.</p>

<p style="text-align: center;"><img alt="List of the two CNAME records and four A records to add at your domain registrar for Blogger" height="720" src="/images/blog/8b6cae9e59b7.png" style="border-radius: 8px; height: auto; max-width: 100%;" width="1200" /></p>

<h2>Step 4: Wait, then save again in Blogger</h2>
<p>DNS changes are not instant. Wait at least an hour, then go back to Blogger and save your custom domain again. If you still get an error, wait longer and retry. It can take up to 24 hours.</p>

<h2>Step 5: Turn on the final settings</h2>
<p>Back in <strong>Settings → Publishing</strong>:</p>
<ul>
  <li>Turn on <strong>Redirect domain</strong>, so the non-www version sends visitors to the www version</li>
  <li>Turn on <strong>HTTPS availability</strong> and <strong>HTTPS redirect</strong>, so your site shows the padlock</li>
</ul>
<p>Your old blogspot.com address will start redirecting to your new domain too.</p>

<h2>Common problems and fixes</h2>
<p><strong>Blogger keeps showing an error.</strong> The most common cause is not waiting long enough. Give it a few hours and try again.</p>
<p><strong>I can’t find my second CNAME.</strong> Enter your domain in Blogger again and click Save. The error screen should show it.</p>
<p><strong>The site works with www but not without.</strong> Check that all four A records are saved and that no old A records are left over.</p>
<p><strong>No padlock, or an HTTPS error.</strong> If your domain has CAA records, add one for <code>letsencrypt.org</code>. Otherwise Blogger can’t issue your free SSL certificate.</p>
<p><strong>Nothing works after 24 hours.</strong> Look for typos in the records and for leftover conflicting records, then contact your registrar’s support.</p>

<h2>Blogger or a website builder: which is better for you?</h2>
<p>Blogger is free and great for a simple blog, but you have limited control over design and features. If you’re building a business site and don’t want to deal with DNS records at all, an AI website builder is a quicker route.</p>
<p>HostAfrica’s AI builder creates a site from a short description of your business, includes hosting, and lets you connect your own domain or register a new one. At the time of writing it costs R29.70 a month for the first three months, then R99 a month, with a 30-day money-back guarantee. It doesn’t do online stores or bookings, so it suits simple business sites best. Prices can change, so confirm on HostAfrica before you order.</p>

<p style="margin: 24px 0; text-align: center;">
  <a href="https://hostafrica.co.za/website-builder/easy-ai-builder/?aff=3166" rel="sponsored noopener" style="background: #1a73e8; border-radius: 6px; color: white; display: inline-block; font-weight: bold; padding: 12px 24px; text-decoration: none;" target="_blank">Try the HostAfrica AI builder →</a>
</p>

<h2>Quick recap</h2>
<ol>
  <li>Enter <code>www.yourdomain.co.za</code> in Blogger’s custom domain setting</li>
  <li>Add both CNAME records at your registrar</li>
  <li>Add the four A records</li>
  <li>Wait, then save again in Blogger</li>
  <li>Turn on the redirect and HTTPS settings</li>
</ol>

<p style="text-align: center;"><img alt="Five steps to connect a custom domain to Blogger: tell Blogger, add CNAME records, add A records, wait, turn on redirect and HTTPS" height="700" src="/images/blog/7eefe7318914.png" style="border-radius: 8px; height: auto; max-width: 100%;" width="1200" /></p>

<h2>Read next</h2>
<ul>
  <li><a href="https://www.kapyamarket.co.za/2026/11/how-to-register-coza-domain-in-south.html">How to Register a .co.za Domain in South Africa</a></li>
  <li><a href="https://www.kapyamarket.co.za/2026/11/how-to-build-website-with-ai-in-south.html">How to Build a Website With AI in South Africa</a></li>
  <li><a href="https://www.kapyamarket.co.za/2026/11/cheap-web-hosting-in-south-africa-2027.html">Cheap Web Hosting in South Africa 2027</a></li>
</ul>

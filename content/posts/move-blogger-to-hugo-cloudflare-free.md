---
title: "How to Move From Blogger to Hugo and Cloudflare (Free Hosting Guide)"
date: 2026-11-15T12:00:00+02:00
draft: false
slug: "move-blogger-to-hugo-cloudflare-free"
url: "/2026/11/move-blogger-to-hugo-cloudflare-free.html"
description: "A beginner-friendly walkthrough for moving a Blogger blog to Hugo and free Cloudflare hosting, keeping your custom domain and your old post addresses."
tags:
  - "Blogger"
  - "Hugo"
  - "Cloudflare"
  - "Website Guides"
cover:
  image: "/images/move-blogger-hugo.png"
  alt: "How to move from Blogger to Hugo and Cloudflare"
  hiddenInSingle: true
---

Blogger is a good place to start a blog, but at some point many bloggers want more control over design, speed and address structure. This guide shows how Kapya Market moved from Blogger to a free setup built on Hugo (a website generator), GitHub (which stores the files) and Cloudflare (which hosts the site), while keeping the same domain and the same post addresses.

![How to move from Blogger to Hugo and Cloudflare](/images/move-blogger-hugo.png)

It is not the right path for everyone, so read the next section before you start.

## Is this right for you?

**It suits you if** you are comfortable copying commands, you want a fast site without a monthly hosting fee, and you do not mind writing posts as text files.

**Skip it if** you want a visual editor like Blogger's, you want plugins and a dashboard (WordPress is a better fit), or you cannot spend a few hours on setup.

Your Blogger blog keeps working until you switch your domain, so you can build and test everything first without risk.

**Costs:** Hugo, Git, GitHub and Cloudflare's free plan cost nothing, and the free plan is enough for a typical small blog. If you use your own domain, you keep paying for its registration as before.

## What you need

- A computer (the commands below are for Windows; Mac and Linux are similar)
- Your Blogger blog and a backup of it
- A free GitHub account
- A free Cloudflare account
- Optional: your own domain name, such as a .co.za address

## Step 1: Back up your Blogger blog

In Blogger, open **Settings**, scroll to **Manage blog**, choose **Back up content** and download the file. You can also use Google Takeout and select Blogger. Keep this file safe, because it contains all your posts.

Also note your post address style. Blogger uses addresses like `/2026/05/post-name.html`. You will recreate them in Step 4 so you do not lose your search rankings.

## Step 2: Install the tools

On Windows, open PowerShell and run:

```
winget install Git.Git
winget install Hugo.Hugo.Extended
```

Close PowerShell, open it again and check both tools:

```
git --version
hugo version
```

Write down your Hugo version. Cloudflare needs it later.

## Step 3: Create the site and add a theme

```
hugo new site myblog
cd myblog
git init
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

Open `hugo.toml` and set your address, title and theme:

```
baseURL = "https://www.yourdomain.co.za/"
title = "Your Blog Name"
theme = "PaperMod"
```

PaperMod is a free, clean blog theme. Run `hugo server` and open http://localhost:1313 to see your empty site.

## Step 4: Move your posts

Each Blogger post becomes one file in `content/posts`. Give every file a header (called front matter) with the title, the date and the old Blogger address in a `url` line:

```
---
title: "My Post Title"
date: 2026-05-10T09:00:00+02:00
slug: "my-post-title"
url: "/2026/05/my-post-title.html"
description: "A short summary for Google."
---
```

The `url` line is what keeps your old addresses working. Copy the address from your live Blogger post exactly.

Tools such as blog2md convert Blogger backups, but newer Google Takeout files do not always work with them. If a converter fails, a short script can read the backup file, or you can copy posts by hand if you only have a few.

Blogger stores posts as HTML, so Hugo needs permission to show it. Add this to `hugo.toml`:

```
[markup.goldmark.renderer]
  unsafe = true
```

If you save a post as an `.html` file, recent Hugo versions block it by default. This setting allows it:

```
[security]
  allowContent = ['! ^text/org$']
```

If part of a post shows as grey code boxes, Markdown is reading indented HTML as code. Saving the post as an `.html` file usually fixes it.

## Step 5: Preview and compare

Run `hugo server` and compare a few posts with your live Blogger blog. Check that the address, the text and the images match.

Your images still load from Google's servers at this point. It is safer to download them into the `static/images` folder and update the links, so they cannot break later.

## Step 6: Put the files on GitHub

Create an empty repository on github.com, then run:

```
"public/" | Out-File .gitignore -Encoding ascii
git add .
git commit -m "First version"
git branch -M main
git remote add origin https://github.com/YOURNAME/myblog.git
git push -u origin main
```

Replace `YOURNAME` and `myblog` with your own details.

## Step 7: Deploy on Cloudflare

1. In the Cloudflare dashboard, open **Workers & Pages** and create an application from your GitHub repository.
2. Set the build command to `hugo` and the deploy command to `npx wrangler deploy`. Leave the root directory empty.
3. Add a build variable called `HUGO_VERSION` with the version you wrote down in Step 2.
4. Add a file called `wrangler.jsonc` to your site folder, then commit and push it:

```
{
  "name": "myblog",
  "compatibility_date": "2026-11-01",
  "assets": {
    "directory": "./public"
  }
}
```

Cloudflare changes its dashboard often. Depending on the screen you see, it may create a Pages project instead. In that case the build command is `hugo`, the output folder is `public`, and you do not need the wrangler file.

When the build finishes, you get a free address ending in `workers.dev` (or `pages.dev`). Test your site there before touching your domain.

## Step 8: Connect your domain

1. Add your domain to Cloudflare on the free plan, and change the nameservers at your registrar to the two that Cloudflare gives you.
2. In Cloudflare's DNS list, delete the old Blogger website records: the four `A` records for the root domain (`216.239.32.21`, `216.239.34.21`, `216.239.36.21` and `216.239.38.21`) and the `www` `CNAME` that points to `ghs.google.com`.
3. **Leave your email records alone** (the MX and TXT records), or your email can stop working.
4. In your Worker's settings, add `www.yourdomain.co.za` as a custom domain.
5. In Blogger, remove the custom domain.

Your site is briefly unreachable between steps 2 and 4, so do them together.

To send the bare domain to `www`, add a proxied `A` record named `@` with the address `192.0.2.1`. Then create a redirect rule from `https://yourdomain.co.za/*` to `https://www.yourdomain.co.za/${1}` with a 301 status. The address is only a placeholder, because visitors are redirected before they reach it.

## Step 9: Protect your Google traffic

- Keep every `url` line exactly as it was on Blogger.
- Add your site to Google Search Console if it is not there yet. If you were verified through a DNS record, keep that record in Cloudflare.
- Submit `https://www.yourdomain.co.za/sitemap.xml`.
- After a week, open the **Pages** report and look for 404 errors. A few are normal after a move. A long list means some post addresses do not match.

## Common problems

- **"Root directory not found" in Cloudflare:** the build settings point to a folder that does not exist. Clear the root directory field.
- **"Hostname already has externally managed DNS records":** the old Blogger records are still in your DNS list. Delete them (Step 8).
- **A post shows 404:** its `url` line does not match the address you are opening. Hugo builds the address exactly as written.
- **Grey code boxes in a post:** see Step 4.
- **"Is a directory" error when previewing:** delete the `public` folder and run `hugo server` again.

## Is it worth it?

For a small blog, a Hugo site on Cloudflare is fast, free to host and fully under your control. The price is that you work with files and commands instead of a visual editor. If you only want to connect a custom domain to your existing Blogger blog, read our guide on [how to connect a .co.za domain to Blogger](/2026/11/how-to-connect-coza-domain-to-blogger.html) instead.

Questions about moving your own blog? Use the [contact page](/p/contact-us.html) and tell us where you got stuck.
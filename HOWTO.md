# Deploy hello-globe to Cloudflare Pages (Git Integration)

This uses **Option B** — Cloudflare watches the GitHub repo and deploys
every push to `master`. No wrangler, no Node.js, nothing extra in Termux.

## 1. Connect GitHub to Cloudflare (one-time)

1. Open [dash.cloudflare.com](https://dash.cloudflare.com) and log in
2. Sidebar → **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
3. Click **Connect GitHub**, authorize Cloudflare, and select `shamshuipo/hello-globe`
4. Click **Begin setup**

## 2. Build Settings

Enter these and click **Save and Deploy**:

| Setting | Value |
|---|---|
| Production branch | `master` |
| Build command | *(leave blank)* |
| Build output directory | `/` |

No build step — Cloudflare just serves the files as-is.

## 3. First Deploy

Cloudflare clones the repo and deploys `index.html`. After ~30 seconds you get
a URL like `hello-globe-<hash>.pages.dev`. Visit it and confirm the globe works.

## 4. Custom Domain: globe.aieira.net

1. In Cloudflare Dashboard → **Workers & Pages** → `hello-globe`
2. Click **Custom domains** → **Set up a custom domain**
3. Enter `globe.aieira.net` → **Continue**

Cloudflare auto-provisions the DNS record and SSL certificate (the `aieira.net`
zone is already on Cloudflare, so this is one click). Wait a minute or two, then:

**https://globe.aieira.net**

### If aieira.net is in a different Cloudflare account

1. From the Pages-owning account, add `globe.aieira.net` as a custom domain
2. Cloudflare detects it's managed elsewhere and shows a CNAME target (e.g. `hello-globe-<hash>.pages.dev`)
3. In the DNS-owning account → DNS → add:
   ```
   Type:  CNAME
   Name:  globe
   Target: hello-globe-<hash>.pages.dev
   Proxy: Proxied (orange cloud on)
   ```

## 5. Ongoing Workflow

Nothing changes in Termux. Commit and push as usual:

```bash
git add index.html
git commit -m "Update globe"
git push
```

Cloudflare detects the push to `master` and deploys automatically — no CLI
command needed. Deployment status is visible in the Cloudflare Dashboard.

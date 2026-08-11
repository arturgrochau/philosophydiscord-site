# Politics & Philosophy — landing site

A fast, static, SEO-optimized one-pager for the Politics & Philosophy Discord.
No build step, no framework — just HTML/CSS, so it loads instantly and crawls perfectly.

Targets the primary keyword **"political philosophy discord"** plus long-tails
(free-speech discord, european politics discord, geopolitics discord, philosophy debate server).

## 1. One edit before deploying

Buy a domain first (a keyword domain helps a little — e.g. `politicalphilosophy.chat`,
`ppdiscord.org`). Then replace every `REPLACE-WITH-YOUR-DOMAIN` with your real
`https://yourdomain` (no trailing slash):

```
cd ~/Projects/pnp-site
grep -rl REPLACE-WITH-YOUR-DOMAIN . | xargs sed -i '' 's#https://politicsphilosophy.com#https://yourdomain.tld#g'
```

Optional: drop a 1200×630 `og.png` (social share image) in this folder.

## 2. Host it — use Cloudflare Pages or GitHub Pages. NOT the M1.

**Honest call (this is the researched best practice, against the "host on M1" instinct):**
a static content site gains *nothing* from being served from home, and the M1 adds real
ranking risk — if the M1 sleeps, the site (and its ranking signal) goes down, and Cloudflare's
**Bot Fight Mode** + **Rocket Loader** can silently block or garble Googlebot with no warning in
Search Console. A brand-new site cannot afford invisible downtime or crawl failures. Put it on a
proper static host; keep the M1 for the bots and the game server.

**Cloudflare Pages — recommended.** Free, instant HTTPS, real domain, zero babysitting.
1. `git init && git add -A && git commit -m "site"` and push to a GitHub repo.
2. Cloudflare dashboard → Pages → connect the repo (build command: none; output dir: `/`).
3. Pages → Custom domains → add your domain (Cloudflare handles DNS + cert).
4. In the Cloudflare zone, **turn OFF Rocket Loader and Bot Fight Mode** so Googlebot is never blocked.

**GitHub Pages — equally fine.** Repo → Settings → Pages → deploy from `main` → add custom domain.

(If you ever *must* self-host on the M1: Cloudflare Tunnel gives a real HTTPS domain without
exposing your home IP — but only with Bot Fight Mode + Rocket Loader OFF and guaranteed 24/7
uptime. It's not worth the fragility here.)

## 3. After it's live — the SEO checklist (do these, in order)

1. **Google Search Console** → add the domain → verify → **submit `sitemap.xml`**. This is how Google finds and trusts the page fastest.
2. **Bing Webmaster Tools** → same (also feeds other engines).
3. **Point every directory + profile at the domain**: put `https://yourdomain` in the Disboard listing, Discadia, top.gg, discord.me, DiscordServers.io, and the Discord server profile / a pinned #rules link. Every one of those is a crawlable link back to your site (authority signals).
4. **Get 2–3 real backlinks**: a genuine Reddit answer in r/philosophy / r/discord_servers style threads ("best philosophy discord?"), a listing on a couple more free directories. Never spam — one honest mention beats fifty spammy ones.
5. **Fill the directory section** in `index.html` with real related servers (name + one-liner + invite). Linking out to genuine communities builds topical relevance and earns reciprocal links.

## Realistic expectation
A brand-new domain takes weeks-to-months to rank, because it has no authority yet.
The FAST wins are the directory listings + the Discord Discovery page (they borrow
discord.com's authority) and the keyword-rich server description — the site is the
durable, compounding asset that pays off over time.

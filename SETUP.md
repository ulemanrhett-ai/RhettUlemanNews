# RhettUlemanNews.com — CMS-ready portfolio

## What is included
- `index.html`: your existing four-photo broadcast homepage, two stacked demo reels, four work sections, About, Contact.
- `content/site.json`: content source read by the public site.
- `admin/`: Decap CMS editor UI and collection configuration.
- `images/`: upload destination for photographs.
- `netlify.toml`: Netlify static-site configuration.

## Deploy to Netlify
1. Create a **private or public GitHub repository** for this website. Do not put credentials in it. Upload the contents of this folder to the root of the repository (not the folder itself).
2. In `admin/config.yml`, replace `YOUR_GITHUB_USERNAME/YOUR_GITHUB_REPOSITORY` with your exact GitHub repository path. Commit the change.
3. In Netlify, choose **Add new project > Import an existing project**, connect GitHub and select the repository. Build command: **leave empty**. Publish directory: `.`. Deploy.
4. Open the Netlify URL to see the public site. The site works before CMS login is configured.
5. **Configure GitHub OAuth for Decap CMS.** Netlify hosting by itself does NOT provide the GitHub OAuth login service. Netlify Identity / Git Gateway should not be assumed available for new sites. Choose a compatible hosted Decap GitHub OAuth provider or deploy a trusted, maintained OAuth proxy, then create/configure the GitHub OAuth application as instructed by that provider. Set `base_url` and `auth_endpoint` in `admin/config.yml` to the provider's documented values, and redeploy. Never put a GitHub OAuth client secret or personal access token in this repository or browser code. Access to edit is governed by GitHub repository permissions and your OAuth configuration.
6. Once OAuth works, visit `https://YOUR-NETLIFY-SITE.netlify.app/admin/`, sign in with GitHub, select **Edit My Website**, and edit photos, reels, and stories. Click **Publish**; Decap commits the changed JSON/media to GitHub, and Netlify redeploys automatically.
7. Purchase `RhettUlemanNews.com` if available. In Netlify **Domain management**, add it as a custom domain and follow Netlify's DNS/HTTPS instructions. Also configure `www` if desired.

## Updating content
- **Homepage photos**: Four Homepage Photos has exactly four slots. Use one photo per slot. Photo Crop Positions controls each crop, e.g. `center 30%`.
- **Demo reels**: paste YouTube/Vimeo links into Latest Demo Reel and Earlier Demo Reel. Embed playback requires the video's owner to allow embedding.
- **Stories**: Add a new item under Stories & Projects, select its category, add a thumbnail, description, and a published link or video link. The site displays it in the matching section.
- **Headshot and resume**: upload through the respective fields.
- **Publishing**: changes are not live until you publish and Netlify finishes redeploying.

## Important notes
- The CMS editor is installed but **login cannot work until the GitHub repository and OAuth provider are configured**. This is a deployment starter, not a pre-connected service.
- Images uploaded to the repo increase its size. Host large demo reels on YouTube or Vimeo rather than uploading huge MP4s to GitHub.
- The public site uses `/content/site.json`, so it should be previewed through a local HTTP server or deployed Netlify site, not opened via `file://`.
- `content/site.json` starts with no sample published projects, so you can add only your real work.
- The editor's **Publish** button commits to your repository; GitHub/Netlify deployment permissions and OAuth are required.

# Deployment

- **`npm run build`:** Creates a production-ready build of your application in the `.nuxt` directory.
- **`npm run start`:** Starts a production server (for SSR).
- **`npm run generate`:** Generates static HTML files (for SSG) in the `dist` directory.
- **Deployment Platforms:**
  - **Netlify, Vercel:** Excellent for static sites (SSG) and provide easy deployments, automatic HTTPS, and CDNs.
  - **Heroku, DigitalOcean, AWS, Google Cloud:** Suitable for server-side rendered (SSR) applications. You'll need to configure a Node.js server to run your application.
  - **Static hosting (S3, Firebase Hosting, GitHub Pages):** Ideal and very cheap for static sites (SSG)

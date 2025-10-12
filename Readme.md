 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index a5de473b47049dfc1c40c795787e5726881c7415..b73c32538cf8e7d99579bef3dbe8ab2a5af798b2 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,102 @@
-# ate
\ No newline at end of file
+# All Trade Electric Inc. Website
+
+A single-page marketing and booking site for an electrical contracting business covering residential and commercial projects.
+
+## Features
+
+- Hero section with quick contact information and calls to action.
+- Service overview, differentiators, and recent project highlights.
+- Appointment booking form with validation and live summary panel.
+- Configurable deposit calculator and external payment link handoff.
+- Responsive design with modern typography and subtle motion.
+
+## Customization
+
+1. Open `index.html` and update business details (name, phone, email, service descriptions, project photos).
+2. In `script.js`, replace the `PAYMENT_LINK` value with your live Stripe, Square, or PayPal checkout link.
+3. Adjust deposit amounts in the `DEPOSIT_MAP` object to match your pricing.
+4. Update colors or typography in `styles.css` to match your branding.
+
+## Local Preview
+
+Open `index.html` directly in a browser, or use a local server:
+
+```bash
+python3 -m http.server 8000
+```
+
+Then visit http://localhost:8000/ in your browser.
+
+## Testing
+
+Automated test suites are not configured for this static site. Validate the
+experience by launching the local preview server above and confirming that the
+booking flow loads without console errors in your browser developer tools.
+
+## Launching the Site
+
+Follow these steps to turn the project into a public-facing website:
+
+1. **Pick a hosting platform.** Any static host works—GitHub Pages, Netlify,
+   Vercel, Cloudflare Pages, and Amazon S3/CloudFront are all popular choices.
+   Create an account and initialize a new static-site project.
+2. **Upload the files.** Deploy `index.html`, `styles.css`, `script.js`, and
+   any assets you add. The HTML now references `styles.css?v=20241013` to bust
+   old caches, so make sure the CSS file is present on the host. On services
+   like Netlify/Vercel you can drag-and-drop the project folder or connect it to
+   this Git repository for automatic builds.
+3. **Secure a custom domain.** Purchase your business domain (for example,
+   `alltradeelectric.com`) through a registrar such as Google Domains, GoDaddy,
+   or Namecheap. If you already own a domain, use the registrar’s DNS dashboard
+   for the next step.
+4. **Point DNS to your host.** In your registrar’s DNS settings, create the
+   records recommended by the hosting provider (typically A or CNAME records).
+   Allow DNS propagation (up to 24 hours), then confirm the domain resolves to
+   the site.
+5. **Enable HTTPS.** Most hosts automatically provision SSL certificates. If
+   yours does not, use Let’s Encrypt or your registrar’s certificate service to
+   ensure visitors see a secure padlock icon.
+6. **Connect payments and email.** Replace the placeholder payment URL in
+   `script.js` with your live checkout link and verify that booking alerts route
+   to `AllTradeElec@gmail.com`. Consider adding an autoresponder so customers
+   receive confirmation instantly.
+7. **Publish ongoing updates.** Document future changes in this repository and
+   redeploy whenever you update services, rates, testimonials, or imagery.
+
+Once these steps are complete, share the domain on business cards, vehicles,
+and social media so customers can book directly through the site.
+
+## Troubleshooting a Live Domain
+
+If you have already pointed a domain such as `alltradeelectric.org` at your
+host but the site shows an error (for example HTTP 403 Forbidden), run the
+status helper:
+
+```bash
+./tools/check_live_status.py
+```
+
+The script reports the HTTP status code and suggests common fixes for a 403
+response, including verifying DNS, ensuring the host has a deployed build, and
+confirming any CDN or firewall rules allow public access. Update your hosting
+configuration until the check reports a successful (200-level) status code.
+
+### If the live site appears unstyled
+
+- Confirm that `styles.css` was uploaded alongside `index.html`.
+- Because some hosts aggressively cache CSS, the HTML references
+  `styles.css?v=20241013`; double-check that query-stringed URL is reachable.
+- The booking script now injects an inline fallback theme when the stylesheet
+  is blocked. If you still see a blank layout, open the browser console to look
+  for 403/404 errors and adjust your hosting configuration so the CSS file can
+  be served normally.
+
+### Latest status checks
+
+- **Timestamp:** 2025-10-12 19:52 UTC
+  - **Result:** Connection blocked before reaching origin — `Tunnel connection failed: 403 Forbidden`
+  - **Next steps:** Confirm the production host allows inbound HTTPS traffic, double-check proxy/CDN firewall rules, and make sure the site is fully deployed for `alltradeelectric.org`.
+- **Timestamp:** 2025-10-12 18:48 UTC
+  - **Result:** Connection blocked before reaching origin — `Tunnel connection failed: 403 Forbidden`
+  - **Next steps:** Confirm the production host allows inbound HTTPS traffic, double-check proxy/CDN firewall rules, and make sure the site is fully deployed for `alltradeelectric.org`.
+
 
EOF
)

 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index a5de473b47049dfc1c40c795787e5726881c7415..971ff666f656cad0bcaff6e4322621315564ee70 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,22 @@
-# ate
\ No newline at end of file
+# All Trade Electric Inc. website
+
+Static marketing site for All Trade Electric Inc., a South Florida electrical
+contractor providing residential and commercial construction, service calls, and
+custom lighting solutions.
+
+## Tech stack
+
+- Plain HTML5, CSS, and vanilla JavaScript
+- Netlify Forms for handling the service request form
+- Responsive layout optimized for mobile and desktop
+
+## Local development
+
+1. Open `index.html` in your browser to preview the site locally.
+2. Edit `styles.css` or `script.js` as needed; the page will reload on refresh.
+
+## Deployment
+
+The project is deploy-ready on Netlify. Drag and drop the repository folder into
+Netlify or connect it to GitHub. No build step is required—Netlify will serve
+`index.html` as the site entry point.
 
EOF
)

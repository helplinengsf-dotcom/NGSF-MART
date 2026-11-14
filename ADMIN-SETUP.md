# NGSF MART Admin Panel Setup

Admin page: https://helplinengsf-dotcom.github.io/NGSF-MART/admin.html

## One-time Cloudflare setup

1. Open Cloudflare Dashboard and select the account that owns the `ngsf-mart` Worker.
2. Open **Workers & Pages** → **ngsf-mart** → **Settings** → **Variables and Secrets**.
3. Add these two variables as **Secrets** (not plain text variables):
   - `ADMIN_BOOTSTRAP_TOKEN` — generate a long random value (at least 32 characters). Keep it private; enter it once in the Admin Panel's First-time Setup form.
   - `SESSION_SIGNING_KEY` — generate a different long random value (at least 32 characters). Keep it private; the Worker uses it to sign admin sessions.
4. Save the secrets and redeploy the Worker if Cloudflare asks.
5. Open the Admin page, choose **First-time Setup**, enter the bootstrap token, the prefilled authorized email `helpline.ngsfmart@gmail.com`, and create a password of at least 12 characters.
6. After setup, use the Login tab. The initial setup endpoint will reject further setup attempts once the first admin exists.

## Current capabilities

- Super Admin login with PBKDF2 password hashing and signed 12-hour sessions.
- Dashboard counts for products, orders, customers and paid sales.
- Product create, edit, publish/hide, category, price, stock, SKU, image URL and description.
- Order list and order-status updates.

## Important

- Keep both Worker secrets private. Never put them in GitHub files or share them in chat.
- Online payment processing, checkout/order creation, customer accounts, image uploads and shipping integration are not enabled yet.
- The store remains separate from all other NGSF websites, databases and admin systems.

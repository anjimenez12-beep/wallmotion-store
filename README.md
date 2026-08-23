# MotionVault 4K

A ready-to-run storefront for selling static and animated 4K wallpapers with PayPal.

## Included
- Responsive premium storefront.
- Filters for Motion / Static wallpapers.
- Admin upload form with protected admin key.
- Separate public preview and private original files.
- Server-side PayPal order creation and capture.
- Server-side price verification.
- Secure 24-hour download token after confirmed payment.

## Run locally
1. Install Node.js 20+.
2. Copy `.env.example` to `.env`.
3. Create a PayPal Developer app and place the **Sandbox Client ID** and **Sandbox Secret** in `.env`.
4. Change `ADMIN_KEY` to a long private password.
5. In this folder run:
   npm install
   npm start
6. Open http://localhost:3000

## Go live
- Set `PAYPAL_ENV=live`.
- Replace credentials with your live PayPal Client ID and Secret.
- Host the Node app on a service that provides persistent disk/storage or adapt the private files to S3/R2/Supabase Storage.
- Use HTTPS.
- For a production store, replace the in-memory download tokens with a database/Redis so links survive server restarts.
- Add Terms, Privacy Policy, Refund Policy, support email and your business/store information.

## Important security design
The browser sends only a product ID. The server reads the product price from its own database before creating the PayPal order. The PayPal secret never goes to the browser. The original wallpaper lives in `storage/private`, not in `public`, and is delivered only through a validated post-payment download token.

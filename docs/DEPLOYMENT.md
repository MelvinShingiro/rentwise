# RentWise deployment plan

This is the deployment plan for the future application. There is no live demo yet.

## Database and authentication

1. Create a project on the [Supabase Free plan](https://supabase.com/pricing).
2. Apply version-controlled database migrations for the schema, access rules, and booking conflict constraints.
3. Configure staff authentication and the application's allowed redirect URLs.
4. Add fictional sample data and verify cross-workspace access is denied.

Use only the Supabase publishable key in frontend configuration. Enable row-level security and never expose a service-role or secret key in the browser.

## Frontend

1. Build the React and TypeScript application with Vite.
2. Connect this GitHub repository to Cloudflare Pages.
3. Set the build command to `npm run build` and output directory to `dist`.
4. Add the Supabase project URL and publishable key as frontend build environment variables.
5. Deploy and configure Supabase Auth to allow the resulting `pages.dev` URL.
6. Test login, inventory edits, booking conflicts, and returns on the deployed demo.

See [Cloudflare's React deployment guide](https://developers.cloudflare.com/pages/framework-guides/deploy-a-react-site/).

## Free-tier limits

Cloudflare Pages offers free static hosting. Supabase Free currently includes a 500 MB database and can pause projects after a week of inactivity. Keep the demo within free quotas and check availability before sharing it. These allowances were checked on October 22, 2026 and can change.

The first release records deposit statuses manually, so no payment-processing or paid messaging service is required.

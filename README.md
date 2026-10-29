# Ticketmaster Android Demo

A Ticketmaster-style Android hackathon demo with event discovery, search, categories, favorites, a mock checkout flow, locally persisted demo orders/tickets, and email-link sharing. This is an independent demonstration and is not affiliated with Ticketmaster. All purchases are simulated and tickets are not valid for entry.

## Features
- Discover and search sample events by name/category/venue
- Category filters and city selection
- Optional Ticketmaster Discovery API integration
- Event detail pages and favorite events
- Standard, Premium, and VIP mock ticket selection
- Calculated ticket subtotal, service fee, tax, and total
- Checkout form validation and simulated order confirmation
- Demo ticket/order reference saved locally across app restarts
- Email event link through the phone's installed email application
- Cloud APK build through GitHub Actions

## Build from a phone using GitHub Actions
1. Create or sign in to a GitHub account.
2. Create a repository and upload the extracted project files and folders, preserving the directory structure (including `.github/workflows/android.yml`).
3. Open **Actions** and enable workflows if prompted.
4. Run **Build Android APK**, or push a commit to the `main` branch.
5. Open the successful workflow run and download the `ticketmaster-demo-apk` artifact.
6. Extract the artifact ZIP to obtain `app-debug.apk`, then install it on your Android phone. Android may ask you to allow installation from the browser or file manager.

The workflow uses GitHub's hosted build environment; Android Studio is not required on your own device. This project has not been verified with a successful Android build in this workspace, so rely on the workflow result to confirm compilation.

## Enable live events
1. Obtain an API key through the official Ticketmaster Discovery API developer portal: https://developer.ticketmaster.com/products-and-docs/apis/discovery-api/v2/
2. In `app/build.gradle.kts`, set `TICKETMASTER_API_KEY` in the `buildConfigField` value.
3. Rebuild the app. Do not embed a private production credential in a publicly distributed APK; use a backend proxy for production and follow API terms and rate limits.

Without a configured API key, the app shows clearly intended sample events. Sample events, prices, and all ticket availability are demonstration data.

## Email behavior
The email button opens an installed email application with a prefilled subject and event details. The user chooses the recipient and taps Send. It does not silently send email. Direct sending would require a secure backend and email service.

## Important limitations
- This is a demo, not the official Ticketmaster app.
- Checkout never charges money or collects payment-card details.
- Demo tickets and their QR-like icon are not valid for venue entry.
- Real ticket inventory, seat maps, ticket issuance, and payments are not integrated.

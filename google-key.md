---
permalink: /google-key
---

<!--
Sources checked 11 Nov 2026:
https://developers.google.com/maps/billing-and-pricing/pricing
https://developers.google.com/maps/billing-and-pricing/pricing-india
https://developers.google.com/maps/get-started
https://developers.google.com/maps/documentation/places/web-service/get-api-key
https://developers.google.com/maps/documentation/routes/get-api-key
https://developers.google.com/maps/api-security-best-practices
https://docs.cloud.google.com/apis/docs/capping-api-usage
https://docs.cloud.google.com/billing/docs/how-to/budgets
-->

# Use your own Google key

Trip planning uses Google Maps data. The app includes a small free allowance. Add your own Google key and trip planning uses **your own free monthly usage from Google** instead. Setup takes about 10 minutes on a computer.

## 1. Create a project with billing

1. Open the [Google Cloud console](https://console.cloud.google.com/projectcreate) and create a project (any name).
2. [Link a billing account](https://console.cloud.google.com/billing/linkedaccount) to it. Google asks for a card even for free usage; you're only charged if you go past the free usage.

## 2. Turn on two services

Open each link with your new project selected and click **Enable**:

- [Places API (New)](https://console.cloud.google.com/apis/library/places.googleapis.com)
- [Routes API](https://console.cloud.google.com/apis/library/routes.googleapis.com)

## 3. Create and lock the key

1. Open [Keys & Credentials](https://console.cloud.google.com/google/maps-apis/credentials) and click **Create credentials → API key**.
2. Open the new key. Under **Application restrictions** pick your phone:

   **Android** — choose **Android apps → Add**, then enter:
   - Package name: `net.johnlazarus.evmileagetracker`
   - SHA-1 fingerprint: `4E:01:70:35:AE:46:6C:6D:0B:ED:0D:62:71:21:0A:65:26:21:C0:3C`

   **iPhone** — choose **iOS apps → Add**, then enter:
   - Bundle ID: `johnlazarus.EV-Mileage-Tracker`

3. Under **API restrictions** choose **Restrict key**, tick **Places API (New)** and **Routes API**, and click **Save**.
4. Copy the key.

Using both an iPhone and an Android phone? Make one key for each.

## 4. Add it to the app

**Settings → Trip planner → Your own Google key** → paste → **Test key**.

## Optional: never pay anything

- **Cap daily use:** in [Quotas](https://console.cloud.google.com/iam-admin/quotas), lower the per-day limit for Places API (New) and Routes API. Google stops requests at that number ([how](https://docs.cloud.google.com/apis/docs/capping-api-usage)).
- **Budget alert:** in [Budgets & alerts](https://console.cloud.google.com/billing/budgets), create a budget so Google emails you if any charge starts ([how](https://docs.cloud.google.com/billing/docs/how-to/budgets)).

Google gives every billing account free usage each month and sets the amounts per country. See the current amounts on [Google's official pricing page](https://developers.google.com/maps/billing-and-pricing/pricing).

## Privacy

Your key stays on your phone, protected by the iPhone Keychain or Android Keystore. It is sent only to Google and nowhere else. Remove it any time from the same screen.

## If it doesn't work

- **Key rejected:** check the package name and SHA-1 (Android) or bundle ID (iPhone) match exactly, and both services are enabled and ticked under API restrictions.
- **Billing not enabled:** link a billing account, wait a few minutes, test again.
- **Daily limit reached:** you hit a cap you set. Raise it in Quotas or wait until tomorrow.

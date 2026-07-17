<!--
  Hosting note (not part of the published document): the vendor will host this file
  verbatim via a public GitHub Pages repository (e.g. portal-capture-legal) and link
  to the rendered page from the Atlassian Marketplace listing's privacy policy field.
  This file intentionally carries no site-specific frontmatter so it can be dropped
  into any static site generator or rendered as plain Markdown/HTML as-is.
-->

# Portal Capture — Privacy Policy

**Last updated:** 2026-07-17

Portal Capture ("the app") is an Atlassian Forge app for Jira Service Management (JSM) that lets customers attach a screen recording or an annotated screenshot to a customer portal request. This policy describes exactly what data the app handles, where it is stored, and what it never does.

## 1. Summary

- The app runs entirely on Atlassian's Forge platform. It has no servers of its own.
- All screen recordings and screenshots are stored **only** as ordinary Jira attachments, inside **your own** Atlassian site. They are never copied, transmitted, or replicated anywhere outside Atlassian's infrastructure.
- The app's own persistent storage (Forge's built-in key-value store) holds only configuration — which project key is used for temporary staging, which service projects have the capture panel enabled, and a cached mapping from portal ID to project key. It never holds recordings, screenshots, or any personal data.
- The app has no analytics, no third-party SDKs, and makes no network calls to anything other than Atlassian's own Jira REST APIs.
- Anonymous portal visitors are fully supported. The app does not require an account, a login, or a browser extension, and it does not create or store an identifier for anonymous visitors — no account ID is ever recorded for them.

## 2. What data the app processes

### 2.1 Screen recordings and screenshots

When a customer uses the capture panel on a JSM portal request form, the app can capture:

- A screen recording (via the browser's screen-sharing and recording APIs), up to 90 seconds long, encoded in the browser before upload.
- A single screenshot frame, optionally annotated by the customer with rectangles, arrows, and text labels drawn on top of the image.

The capture is uploaded from the customer's browser to the app's backend in small chunks and stored as a Jira attachment on a temporary staging record inside your Atlassian site. When the customer submits their request, the app automatically moves the finished attachment onto the newly created request and deletes the temporary copy. If a capture is started but the request is never submitted, the temporary copy is automatically deleted after 24 hours.

At no point does this data leave Atlassian's infrastructure. The app does not upload, mirror, or transmit captures to any server, cloud storage bucket, or third party outside Atlassian.

### 2.2 Reporter environment metadata

When a capture is successfully attached to a request, the app posts an **internal** comment (visible only to your agents, never to the customer) recording basic environment information the customer's browser makes available: browser/user-agent string, operating system, screen viewport size, timezone, and locale. This is the same category of information any web application can read from a visiting browser; the app does not use it for tracking, does not combine it with an identity, and does not send it anywhere beyond the Jira issue it's commented on.

### 2.3 Configuration data

Site administrators configure the app through a settings page in Jira. This configuration — which project holds temporary staged uploads, and which service projects have the capture panel turned on — is stored in Forge's built-in application storage, scoped to your Atlassian site. This storage never contains recordings, screenshots, or any data about individual customers or requests.

### 2.4 What the app does not collect

- No account IDs, email addresses, or names are recorded for anonymous portal visitors.
- No analytics or usage-tracking data is collected by the app.
- No cookies, fingerprinting, or cross-site tracking of any kind.
- No data is sold, shared with advertisers, or used to build profiles of any kind.

## 3. Where data is stored

All data the app produces or handles is stored using Atlassian's own Forge platform primitives:

- **Jira attachments** — screen recordings and screenshots, stored on issues inside your Atlassian site, subject to your site's own data residency, retention, and access-control settings.
- **Forge application storage (KVS)** — configuration only, as described in §2.3, scoped to your Atlassian site.

The app has no database, file store, or server infrastructure of its own. It cannot store data anywhere other than the two locations above, both of which live inside your Atlassian site.

## 4. Who can access the data

- **Screen recordings and screenshots** become normal Jira attachments on the created request, visible to whichever agents and customers your existing JSM permission scheme already allows to see that request's attachments. The app does not change or bypass your existing Jira permissions.
- **The internal reporter-environment comment** (§2.2) is marked internal and is visible to agents only — it is never shown to the portal customer.
- **Configuration data** (§2.3) is visible only to users with access to the app's admin settings page (Jira administrators).

## 5. Third parties

Portal Capture does not integrate with, transmit data to, or rely on any third-party service. Its only network calls are to Atlassian's own Jira Cloud REST APIs, made using the Forge platform's built-in `asApp()` authentication. No data is processed by any vendor other than Atlassian itself.

## 6. Data retention and deletion

- Recordings and screenshots persist as Jira attachments for as long as the issue they're attached to exists, governed by your site's own attachment and issue retention settings.
- Temporary staged uploads (captures made before the customer submits their request) are deleted automatically once the request is created, or after 24 hours if the request is never submitted.
- Uninstalling the app removes its configuration storage. It does not retroactively delete attachments already placed on issues, since those are ordinary Jira attachments owned by your site.

## 7. Children's privacy

The app is intended for use by businesses and their customers in a business support context and is not directed at children. It does not knowingly collect data from children.

## 8. Changes to this policy

If this policy changes, the updated version will be published at the same URL with a revised "Last updated" date.

## 9. Contact

Questions about this policy or how Portal Capture handles data can be sent to:

**alenkomras@gmail.com**

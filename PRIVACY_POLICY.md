# Privacy Policy for Watchmarker for YouTube

**Effective Date:** September 10, 2026

**Last Updated:** September 10, 2026

## Overview

Watchmarker for YouTube ("the Extension") is designed to help you track and mark YouTube videos you have watched. This Privacy Policy explains what information the Extension collects, how we use it, and your rights regarding your data.

## 1. What Information We Collect

### 1.1 Local Watch History Data

The Extension automatically collects and stores the following information locally on your device:

- **Video IDs**: 11-character YouTube video identifiers
- **Video Titles**: Titles of videos you watch
- **Watch Timestamps**: Unix timestamps indicating when you last watched each video
- **View Count**: The number of times you've viewed each video

This data is stored exclusively in your browser's local IndexedDB database and never leaves your device unless you explicitly enable cloud synchronization (see Section 2 below).

### 1.2 User Settings and Preferences

The Extension stores your configuration settings locally, including:

- Visualization preferences (fade-out, grayscale, badge display)
- Tracking settings (which sources to monitor)
- Synchronization preferences
- Stylesheet customizations

### 1.3 Video Detection and Tracking Methods

We collect watch history data through the following mechanisms:

#### YouTube Page Interaction Detection
- Monitoring clicks on video links within YouTube's user interface
- Parsing video URLs from the pages you visit

#### Browser Navigation Tracking
- Observing tab title changes when you navigate to YouTube videos
- Extracting video IDs and titles from page metadata
- **You can disable this** via the extension settings (`idCondition_Brownnav`)

#### Video Progress Monitoring
- Intercepting YouTube's internal watchtime API calls to detect when you're actively watching
- **You can disable this** via the extension settings (`idCondition_Youprog`)

#### Like/Dislike Interaction Detection
- Detecting when you rate videos (like/dislike button clicks)
- Only marks video as watched if you engage with rating buttons

#### Browser History Synchronization
- Importing YouTube videos from your browser's native history
- Extracting timestamps and view counts from Chrome/Edge history
- **You can disable this** via the extension settings (`idCondition_Browser`)

#### YouTube Account History Import
- Optionally importing your authenticated YouTube watch history
- Requires your YouTube authentication through Google accounts
- **You control this** through the extension's YouTube sync settings
- You can choose to import only liked videos (`idCondition_Liked`)

### 1.4 Non-Collected Information

The Extension **explicitly does not collect**:

- ❌ Your real name or email address (unless you opt-in to cloud sync)
- ❌ IP addresses or location data
- ❌ Device identifiers or hardware information
- ❌ Browsing data outside of YouTube
- ❌ Telemetry or analytics data
- ❌ Cross-site tracking information
- ❌ Personally identifiable information (PII)
- ❌ Cookie tracking beyond YouTube authentication
- ❌ Behavioral targeting data

---

## 2. Cloud Synchronization (Optional Feature)

### 2.1 When Cloud Sync is Disabled (Default)

By default, all data remains on your local device. No data is sent to any external servers.

### 2.2 When Cloud Sync is Enabled

If you choose to enable cloud synchronization with Supabase, the following occurs:

#### What Gets Synced
- Video IDs, titles, and watch counts
- Watch timestamps
- Your synchronization preferences

#### What Does NOT Get Synced
- Browser history
- Your real name or personal identifiers
- Any data you specifically mark as private

#### Data Security and Encryption
- Your Supabase credentials are encrypted locally before storage using WebEncryption
- Credentials are stored securely in `chrome.storage.local`
- Session tokens are stored separately in temporary `chrome.storage.session`
- All communication with Supabase uses HTTPS
- Data in transit is protected by SSL/TLS encryption

#### Your Control
- **You control whether cloud sync is enabled** - it is off by default
- **You choose your own Supabase project** - you provide the credentials
- **You can disable at any time** - simply turn off the sync toggle
- **You can delete cloud data** - use the extension's data management options
- **You can export or import data** - full control over your watch history

### 2.3 Supabase Data Storage

When you enable cloud synchronization:

- Your watch history is stored in a PostgreSQL database on Supabase servers
- Each record is associated with your unique Supabase user ID
- Supabase implements Row-Level Security (RLS) policies that ensure:
  - Only you can view your own watch history
  - Only you can modify your own watch history
  - No one else can access your data, not even Supabase support staff without explicit authorization
  - Data is automatically deleted if you delete your Supabase account

#### Supabase Privacy
- Supabase is a third-party cloud provider
- Their privacy practices are governed by their own [Privacy Policy](https://supabase.com/privacy)
- We recommend reviewing Supabase's privacy policy before enabling cloud sync
- Data stored on Supabase is subject to applicable data protection laws

### 2.4 Supabase Authentication Credentials

If you use cloud sync, you must provide:

- Your Supabase Project ID
- Your Supabase Publishable Key (public authentication key)
- Your Supabase email and password (for authentication)

#### Security Practices
- **Secret and service-role keys are forbidden** - the Extension only accepts publishable keys
- Passwords are encrypted before local storage
- Credentials are never transmitted to the Extension developer
- Credentials remain under your control in your browser
- You can revoke access at any time by deleting the configuration in the Extension

---

## 3. User Controls and Privacy Settings

### 3.1 Granular Tracking Controls

You have complete control over what the Extension tracks:

| Setting | What It Controls | Default |
|---------|------------------|---------|
| `idCondition_Brownnav` | Track videos via browser navigation | Enabled |
| `idCondition_Youprog` | Track watch progress via YouTube API | Enabled |
| `idCondition_Yourating` | Only mark videos you rate | Disabled |
| `idCondition_Liked` | Only import liked videos from YouTube | Disabled |
| `idCondition_Browser` | Sync from browser history | Enabled |

**You can modify any of these settings** through the Extension's options page.

### 3.2 Data Access

You can access your data at any time by:

- Viewing your watch history through the Extension's search interface
- Exporting your entire watch history as JSON
- Using the browser's built-in storage inspection tools (DevTools → Application → IndexedDB)

### 3.3 Data Deletion

You can delete:

- Individual videos from your watch history
- Your entire watch history (Database Reset)
- Cloud synchronization data (if enabled)
- Your Supabase credentials to stop cloud sync

All deletions are permanent and irreversible.

### 3.4 Opting Out

You can:

- **Disable the Extension** - Use your browser's extension management page
- **Uninstall the Extension** - All data is deleted with the browser's uninstall process
- **Disable individual tracking methods** - Turn off specific tracking settings
- **Disable cloud sync** - Turn off the Supabase sync feature

---

## 4. Data Retention

### 4.1 Local Data (IndexedDB)

Local watch history is retained indefinitely until you:

- Manually delete individual videos
- Reset the entire database
- Uninstall the Extension
- Clear your browser's storage

### 4.2 Cloud Data (Supabase)

If cloud sync is enabled, data is retained on Supabase servers according to:

- Your retention settings configured in the Extension
- Supabase's data retention policies
- Automatic deletion when you delete your Supabase account

You can request deletion of cloud data at any time through the Extension's interface.

---

## 5. Third-Party Services

### 5.1 Supabase (Optional)

- **Service**: Cloud database hosting
- **When Used**: Only if you enable cloud synchronization
- **Data Shared**: Video IDs, titles, timestamps, view counts (associated with your Supabase user ID)
- **Their Privacy Policy**: [Supabase Privacy Policy](https://supabase.com/privacy)
- **Your Control**: You choose whether to use this service; you provide your own Supabase project credentials

### 5.2 YouTube API (Optional)

- **Service**: YouTube video metadata and history retrieval
- **When Used**: When you use the "Sync YouTube History" feature
- **Data Used**: Your YouTube authentication (via cookies)
- **Data Shared**: Only your own YouTube watch history is accessed
- **Your Control**: You choose whether to use this feature
- **Note**: All YouTube API calls originate from your browser, not from our servers

### 5.3 Google Authentication (Optional)

- **Service**: Google account authentication for YouTube sync
- **When Used**: When syncing YouTube watch history
- **Data Shared**: YouTube authentication credentials (already in your browser via Google)
- **Their Privacy Policy**: [Google Privacy Policy](https://policies.google.com/privacy)

### 5.4 Microsoft Edge Browser Storage APIs

- **Service**: Browser's native storage APIs (`chrome.storage`, IndexedDB, `chrome.cookies`)
- **When Used**: Always, for storing settings and watch history
- **Data Shared**: None - storage is local to your browser
- **Note**: This is first-party storage, not transmitted to external servers

---

## 6. Data Security and Protection

### 6.1 Local Storage Security

- Data is stored in your browser's IndexedDB
- Protected by browser sandboxing and same-origin policy
- Accessible only by this Extension

### 6.2 Cloud Storage Security

- All communication uses HTTPS/TLS encryption
- Supabase implements encryption at rest
- Row-Level Security (RLS) prevents unauthorized access
- Credentials are encrypted using WebEncryption before local storage

### 6.3 Credential Protection

- Supabase credentials are encrypted before local storage
- Passwords are never displayed in plaintext
- Session tokens are kept separate and temporary
- No credentials are sent to external servers (except Supabase)

### 6.4 What We Don't Do

- ❌ We never sell your data
- ❌ We never share your data with advertisers
- ❌ We never use your data for tracking across websites
- ❌ We never broker your data to third parties
- ❌ We don't collect behavioral tracking information
- ❌ We don't use cookies for advertising or tracking

---

## 7. Permissions Requested and Why

The Extension requests the following permissions, all necessary for core functionality:

| Permission | Why We Need It | How It's Used |
|-----------|----------------|--------------|
| `storage` | Store watch history and settings | Stores data locally in IndexedDB and settings |
| `alarms` | Schedule automatic sync | Schedules background synchronization tasks |
| `history` | Access browser history | Optional browser history import feature |
| `tabs` | Monitor navigation | Tracks when you navigate to video pages |
| `cookies` | Access YouTube authentication | Authenticates with YouTube API for history sync |
| `webRequest` | Monitor watch progress | Detects when you're actively watching videos |

**Host Permissions:**
- `https://www.youtube.com/*` - Inject content scripts on YouTube pages
- `https://m.youtube.com/*` - Support for mobile YouTube
- `https://*.supabase.co/*` - Connect to your Supabase project (only if cloud sync enabled)

---

## 8. Your Rights

### 8.1 Access

You have the right to access your watch history data at any time through the Extension's interface.

### 8.2 Correction

You can correct inaccurate data by:

- Deleting videos and re-importing them
- Manually editing settings

### 8.3 Deletion

You can delete:

- Individual videos
- Your entire watch history
- Your Supabase credentials
- All Extension data upon uninstallation

### 8.4 Portability

You can export your watch history in JSON format for use with other tools.

### 8.5 Opt-Out

You can disable any tracking feature through settings or uninstall the Extension entirely.

---

## 9. Policy Changes

We may update this Privacy Policy to reflect:

- New features or functionality
- Changes in data handling practices
- Legal or regulatory changes
- Technical security improvements

**When we make material changes**, we will:

- Update the "Last Updated" date at the top of this policy
- Notify users of significant changes
- Obtain consent for material changes affecting privacy

---

## 10. Compliance and Applicable Laws

This Privacy Policy complies with:

- Microsoft Edge Add-ons Developer Policies
- GDPR (General Data Protection Regulation) - for EU users
- CCPA (California Consumer Privacy Act) - for California residents
- Other applicable data protection laws

Your data rights under these laws are preserved. The Extension implements technical measures to support these rights.

---

## 11. Contact and Support

### Questions About This Policy

If you have questions about this Privacy Policy or our data practices, you can:

- Visit the Extension's GitHub repository: https://github.com/widike/youtube-watchmarker
- Review the Extension's source code for verification
- Open an issue on GitHub for privacy-related questions

### Privacy Issues

If you believe we have violated your privacy rights or this policy, you can:

- Report the issue on GitHub
- Contact the Extension developer through the Microsoft Edge Add-ons website
- File a complaint with your local data protection authority

---

## 12. Transparency and Open Source

This Extension is open source and published on GitHub. You can:

- Review all source code to verify our data practices
- Check exactly what permissions are requested
- Verify that data handling matches this policy
- Compile the Extension yourself if desired

**Repository**: [youtube-watchmarker on GitHub](https://github.com/widike/youtube-watchmarker)

---

## 13. Summary

**What we collect**: YouTube video IDs, titles, timestamps, and view counts

**Where it's stored**: Your local browser by default; optionally on your Supabase project

**What we share**: Nothing, unless you enable Supabase cloud sync

**What you control**: Everything - tracking settings, cloud sync, data deletion, export, and more

**What we don't do**: Sell data, track you across sites, serve ads, or collect PII

---

**This Extension prioritizes your privacy. You maintain complete control over your watch history data.**

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-09-10 | Initial privacy policy |

---

*Last Updated: September 10, 2026*

*This Privacy Policy is provided to comply with Microsoft Edge Add-ons Developer Policies and applicable data protection regulations.*

# software-construction-mobile-app: Instagram

Group Members and Roles.
- Coordinator: Lufene Mark Travis - Kept the group on track and facilitated discussions.
- App Analyst: Puoch Mabor Makuei - Led feature identification and overview.
- Systems Thinker: Absolom Orianga - Focused on backend and architecture reasoning.
- Risk & Change Analyst: Sebata Allan Kagimu - Focused on maintainability and challenges.
- Documentation Lead: Mubiru Humphery - Ensured clarity and structure in README.

All members contributed jointly to discussions, research, and writing.

Part A: Understanding the App

 1. App Overview
- What problem does this app solve?  
  Instagram solves the problem of sharing visual content (photos and videos) in a social network, allowing users to connect, express themselves, and discover content from others. It facilitates social interaction through likes, comments, and direct messaging, while also supporting content creation with features like filters and editing tools.

- Who are its primary users?  
  Primary users include individuals aged 18-45, content creators, influencers, Sports media, businesses for marketing, and general social media users worldwide. In 2026, it has over 2 billion monthly active users, with a focus on younger demographics and mobile-first audiences.


Part B: Thinking Behind the Scenes

For each feature, we discuss the likely software components involved (UI, Business Logic, Network/APIs, Data Storage), whether it requires internet connectivity, and what might happen if the network is slow or unavailable. Our reasoning is based on logical analysis of Instagram's architecture, which uses microservices, React Native for the frontend, Django/Python for backend, and databases like PostgreSQL and Cassandra.

 Login/Authentication
- Software Components: 
  - UI: Login screen with input fields and buttons.
  - Business Logic: Validation of credentials and session management.
  - Network/APIs: Calls to authentication servers (e.g., via REST APIs) for verification.
  - Data Storage: User credentials stored in secure databases.
- Requires Internet? Yes, to verify credentials with servers.
- If Network Slow/Unavailable: App may show cached last login or offline mode, but new logins fail; could display error messages or allow limited guest access.

 Feed Browsing
- Software Components: 
  - UI: Scrollable list with images/videos.
  - Business Logic: Algorithm for personalizing feed based on user interactions.
  - Network/APIs: Fetches data from feed generation services.
  - Data Storage: Caches recent feeds locally; uses databases for user follows and content metadata.
- Requires Internet? Yes, for fresh content; cached for offline.
- If Network Slow/Unavailable: Loads cached posts; may show stale content or "No internet" banner; refreshes fail.
  
 Posting Content
- Software Components: 
  - UI: Camera/upload interface with editing tools.
  - Business Logic: Image processing, caption parsing.
  - Network/APIs: Uploads to media services via APIs.
  - Data Storage: Media stored in cloud (e.g., S3), metadata in DBs.
- Requires Internet? Yes, for uploading.
- If Network Slow/Unavailable: Queues upload for later; shows progress bar or error; local drafts possible.

   Stories
- Software Components: 
  - UI: Circular icons at top, swipeable views.
  - Business Logic: Expiration logic (24 hours).
  - Network/APIs: Fetches and uploads via dedicated services.
  - Data Storage: Temporary storage with TTL (time-to-live).
- Requires Internet? Yes.
- If Network Slow/Unavailable: Views cached stories; new ones can't be added or viewed live.

 Reels
- Software Components: 
  - UI: Video editor and player.
  - Business Logic: Recommendation algorithms using ML.
  - Network/APIs: Video processing and distribution.
  - Data Storage: Videos in distributed storage.
- Requires Internet? Yes.
- If Network Slow/Unavailable: Plays downloaded reels; creation limited to local editing.

 Direct Messaging (DMs)
- Software Components: 
  - UI: Chat interface.
  - Business Logic: Message encryption and delivery.
  - Network/APIs: Real-time APIs (e.g., WebSockets).
  - Data Storage: Messages in databases.
- Requires Internet? Yes.
- If Network Slow/Unavailable: Shows offline status; unsent messages queued.

 Notifications
- Software Components: 
  - UI: Bell icon with list.
  - Business Logic: Event triggering (likes, etc.).
  - Network/APIs: Push notifications via services like FCM.
  - Data Storage: Notification logs in DBs.
- Requires Internet? Yes for real-time.
- If Network Slow/Unavailable: Delays delivery; shows pending notifications when back online.

  Part C: Change and Maintainability

Chosen Change Scenario: Add Mobile Payments in Uganda
This involves integrating local mobile money systems (e.g., MTN MoMo, Airtel Money) for in-app purchases, shopping, or tipping creators.

- Which parts of the app would need changes?
UI: Add payment buttons in shopping/stories/reels. Business Logic: Integrate with Ugandan payment APIs. Network/APIs: New endpoints for transactions. Data Storage: Secure storage for payment details.

- What existing features could break?
Shopping tags or checkout flows might conflict with new payment gateways. Notifications could overload if transaction alerts are added. Feed algorithms might need adjustment for payment-related content.






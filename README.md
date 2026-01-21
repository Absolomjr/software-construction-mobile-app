# software-construction-mobile-app: Instagram

Group Members and Roles.

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


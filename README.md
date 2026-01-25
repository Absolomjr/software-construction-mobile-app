# software-construction-mobile-app: Instagram

Group Members and Roles.
- Coordinator: Lufene Mark Travis (S23B23/032) - Kept the group on track and facilitated discussions.
- App Analyst: Puoch Mabor Makuei (S23B23/055) - Led feature identification and overview.
- Systems Thinker: Absolom Orianga (S23B23/075) - Focused on backend and architecture reasoning.
- Risk & Change Analyst: Ssebatta Allan Kagimu (S23B23/057) - Focused on maintainability and challenges.
- Documentation Lead: Mubiru Humphery (S23B23/035) - Ensured clarity and structure in README.

All members contributed jointly to discussions, research, and writing.

## Part A: Understanding the App

**App Analyzed:** Instagram  
**Role:** App Analyst – Puoch Mabor Makuei

### 1. App Overview

**What problem does this app solve?**  
Instagram solves the problem of visual-first communication at scale. Before platforms like Instagram, sharing photos or videos required fragmented tools or private messaging. Instagram brings creation, editing, publishing, and discovery of visual content into a single mobile-first platform.

Beyond sharing, Instagram addresses content discovery and engagement. Users are continuously shown content aligned with their interests through personalized feeds, stories, and reels. For creators and businesses, Instagram acts as a distribution and marketing platform where attention can be converted into influence, reach, or income. In practice, Instagram functions as both a social network and a large-scale content delivery system.

**Who are its primary users?**  
Instagram's primary users are mobile-first individuals, largely between the ages of 18–34. These include casual users sharing daily moments, content creators building personal brands, influencers monetizing audiences, and businesses marketing products and services.

In regions such as Uganda and across Africa, Instagram is also widely used by small businesses, freelancers, and creatives as a lightweight alternative to full websites. This makes the platform socially relevant and economically important, especially in mobile-dominated markets.

---

### 2. Core Features

The following features define Instagram's core functionality:

- **User Authentication & Profiles**  
  Users create accounts, log in securely, and manage profiles that represent their identity on the platform. Profiles consolidate posts, followers, bios, and activity history.

- **Personalized Feed Browsing**  
  Instagram displays a dynamic feed of posts from followed accounts and recommended content. The feed adapts based on user interactions such as likes, comments, shares, and watch time.

- **Content Creation & Posting**  
  Users can upload photos and videos, apply filters, edit media, write captions, tag users, and add locations. This feature lowers the barrier to content creation.

- **Stories**  
  Stories allow temporary photo or video posts that disappear after 24 hours. They support interactive elements like polls, questions, and reactions, encouraging frequent and informal sharing.

- **Reels (Short-form Video)**  
  Reels enable users to create and consume short, engaging videos designed for discovery beyond their follower base. This feature is central to Instagram's growth and engagement strategy.

- **Direct Messaging (DMs)**  
  Instagram includes private messaging for one-on-one and group conversations, supporting text, images, videos, voice notes, and shared posts.

- **Notifications & Activity Tracking**  
  Notifications inform users about likes, comments, follows, mentions, and messages, creating a feedback loop that drives continued engagement.


## Part B: Thinking Behind the Scenes

For each feature, we discuss the likely software components involved (UI, Business Logic, Network/APIs, Data Storage), whether it requires internet connectivity, and what might happen if the network is slow or unavailable. Our reasoning is based on logical analysis of Instagram's architecture, which uses microservices, React Native for the frontend, Django/Python for backend, and databases like PostgreSQL and Cassandra.

 **Login/Authentication**
- Software Components: 
  - UI: Login screen with input fields and buttons.
  - Business Logic: Validation of credentials and session management.
  - Network/APIs: Calls to authentication servers (e.g., via REST APIs) for verification.
  - Data Storage: User credentials stored in secure databases.
- Requires Internet? Yes, to verify credentials with servers.
- If Network Slow/Unavailable: App may show cached last login or offline mode, but new logins fail; could display error messages or allow limited guest access.

 **Feed Browsing**
- Software Components: 
  - UI: Scrollable list with images/videos.
  - Business Logic: Algorithm for personalizing feed based on user interactions.
  - Network/APIs: Fetches data from feed generation services.
  - Data Storage: Caches recent feeds locally; uses databases for user follows and content metadata.
- Requires Internet? Yes, for fresh content; cached for offline.
- If Network Slow/Unavailable: Loads cached posts; may show stale content or "No internet" banner; refreshes fail.
  
 **Posting Content**
- Software Components: 
  - UI: Camera/upload interface with editing tools.
  - Business Logic: Image processing, caption parsing.
  - Network/APIs: Uploads to media services via APIs.
  - Data Storage: Media stored in cloud (e.g., S3), metadata in DBs.
- Requires Internet? Yes, for uploading.
- If Network Slow/Unavailable: Queues upload for later; shows progress bar or error; local drafts possible.

 **Stories**
- Software Components: 
  - UI: Circular icons at top, swipeable views.
  - Business Logic: Expiration logic (24 hours).
  - Network/APIs: Fetches and uploads via dedicated services.
  - Data Storage: Temporary storage with TTL (time-to-live).
- Requires Internet? Yes.
- If Network Slow/Unavailable: Views cached stories; new ones can't be added or viewed live.

 **Reels**
- Software Components: 
  - UI: Video editor and player.
  - Business Logic: Recommendation algorithms using ML.
  - Network/APIs: Video processing and distribution.
  - Data Storage: Videos in distributed storage.
- Requires Internet? Yes.
- If Network Slow/Unavailable: Plays downloaded reels; creation limited to local editing.

 **Direct Messaging (DMs)**
- Software Components: 
  - UI: Chat interface.
  - Business Logic: Message encryption and delivery.
  - Network/APIs: Real-time APIs (e.g., WebSockets).
  - Data Storage: Messages are in databases.
- Requires Internet? Yes.
- If Network Slow/Unavailable: Shows offline status; unsent messages queued.

 **Notifications**
- Software Components: 
  - UI: Bell icon with list.
  - Business Logic: Event triggering (likes, etc.).
  - Network/APIs: Push notifications via services like FCM.
  - Data Storage: Notification logs in DBs.
- Requires Internet? Yes for real-time.
- If Network Slow/Unavailable: Delays delivery; shows pending notifications when back online.

   **Explore, Search & Map-Based Discovery (Instagram Maps)**

  - Software Components:
    - UI: Search tab, explore grid, and interactive map interface showing posts by location.
    - Business Logic: Ranking logic for trending places, location-based filtering, and relevance scoring.
    - Network/APIs: Location services, search APIs, and geospatial queries to fetch nearby or tagged content.
    - Data Storage: Location metadata are linked to posts, places, and businesses stored in databases with geospatial indexing.

  - Requires Internet? Yes, especially for real-time discovery and map updates.

  - If Network Slow/Unavailable: Previously loaded explore content may appear, but map interactions, nearby place discovery, and live search results will fail or load slowly.

 ## Part C: Change and Maintainability

Chosen Change Scenario: Add Mobile Payments in Uganda
This involves integrating local mobile money mediums and systems (e.g., MTN MoMo, Airtel Money) for in-app purchases, shopping, or tipping creators.

- Which parts of the app would need changes?
  
UI: Add payment buttons in shopping/stories/reels. Business Logic: Integrate with Ugandan payment APIs. Network/APIs: New endpoints for transactions. Data Storage: Secure storage for payment details.

- What existing features could break?
  
Shopping tags or checkout flows might conflict with new payment gateways. Notifications could overload if transaction alerts are added. Feed algorithms might need adjustment for payment-related content.

- Why would this change be difficult to implement?
  
Regulatory compliance with Uganda's payment laws and taxes (e.g., mobile money tariffs). High fraud risks require enhanced security. Integration with fragmented mobile money providers; poor network in rural areas could cause failures. User education on fees and safety; testing across devices in Uganda's market.

## Part D: Software Construction Challenges

Here are 5 engineering challenges in maintaining or improving Instagram, with brief explanations:

- Performance and Scalability: Handling billions of users requires efficient load balancing and sharding; spikes in traffic (e.g., viral reels) can overload servers.
- Security and Data Privacy: Protecting against hacks, leaks, and complying with global regs like GDPR; features like DMs need end-to-end encryption.
- Testing Across Devices and OS Versions: Android/iOS fragmentation means extensive testing; memory leaks on low-end devices can crash the app.
- Backward Compatibility: Updates must support old app versions; changing APIs can break third-party integrations.
- Reliability Under Poor Network Conditions: In areas like Uganda, apps must handle intermittent connectivity with caching and offline modes.

 ## Part E: Group Reflection

1. What surprised your group most about the complexity behind this app?  
   The sheer scale of microservices and ML for recommendations; we didn't realize how much asynchronous processing is needed for uploads and feeds.

2. Why is writing “working code” not enough for software systems at this scale?  
   At scale, code must be maintainable, scalable, and resilient; issues like downtime affect millions, requiring monitoring, testing, and architecture focus.

3. What did you learn about teamwork from this exercise?  
   Dividing roles helped efficiency, but collaboration ensured balanced insights; remote tools like GitHub mimic real software teams.

**Group Contributions**
- Mark Travis Lufene: Coordinated meetings, contributed to Parts A and E.
- Puoch Mabor Makuei: Researched features, wrote Part A.
- Absolom Orianga: Analyzed architecture, contributed to Part B.
- Allan Kagimu Ssebatta: Handled challenges, wrote Parts C and D.
- Humphery Mubiru: Structured document, contributed to part C and D, edited for clarity.

All members reviewed and approved the final content of this document.




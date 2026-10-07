VORO V0.0.1 — MASTER PROJECT SPECIFICATION

1. PROJECT IDENTITY

Project Name: VORO
Version: V0.0.1
Project Type: Modern Video Platform
Architecture: Flutter + Android + Supabase
Current Scope: V0.0.1 only

VORO is being built as a modern video platform designed to become a scalable platform capable of competing with major video platforms.

The owner is the CEO and final decision-maker for the project.

This document is the official source of truth for VORO V0.0.1.

---

2. SOURCE OF TRUTH

The project must follow this specification exactly.

Rules:

- VORO V0.0.1 has exactly 14 official phases.
- Do not create a different roadmap.
- Do not introduce phases outside these 14 phases.
- Do not mix V0.0.1 with V0.0.2 or V0.0.3.
- Do not invent unapproved features or business rules.
- Do not replace the architecture without first inspecting the existing project and dependencies.
- Do not perform unnecessary full rewrites.
- Preserve working functionality.
- Large or destructive architectural changes require explicit owner approval.
- The implementation must be real, not a mock demonstration.
- Do not claim a phase is complete unless it is actually implemented and tested.

---

3. OFFICIAL VERSION STRUCTURE

V0.0.1

Core MVP and complete foundational platform.

V0.0.2

Product Expansion / Social Platform Expansion.

V0.0.3

VORO Identity / Advanced Systems.

Only V0.0.1 is in scope for this project.

Do not implement V0.0.2 or V0.0.3 features unless explicitly requested by the owner.

---

4. TECHNOLOGY STACK

Mobile

- Flutter
- Dart
- Android
- Android Studio
- VS Code

Backend

- Supabase
- PostgreSQL
- Supabase Auth
- Supabase Storage
- Row Level Security (RLS)
- Backend/server-side authorization

The application must be designed so that the backend remains the authority for security and permissions.

Flutter must never be treated as the final security layer.

---

5. CORE ARCHITECTURE PRINCIPLES

Security

Never rely on:

- Hidden Flutter buttons
- Hidden screens
- Client-side permission checks
- Hard-coded administrator credentials
- Hard-coded owner email
- Hard-coded owner username
- Hard-coded secret passwords
- Service-role credentials inside the mobile application

Security must be enforced through:

- Supabase Auth
- PostgreSQL
- RLS
- Storage policies
- Backend authorization
- Ownership checks
- Server-side permission validation

Correct security model:

USER AUTH
→ SUPABASE
→ ROLE / PERMISSION
→ RLS / BACKEND AUTHORIZATION
→ OPERATION

---

6. IMPORTANT BUSINESS DISTINCTIONS

These distinctions are mandatory.

Feature ≠ Navigation

A feature can exist without being a permanent navigation tab.

Role ≠ Permission

A user's ability to perform an operation must be controlled by backend permissions.

Upload Access ≠ Monetization Eligibility

A normal registered user may upload and publish videos.

Monetization eligibility is a separate system.

Advertising System ≠ Advertiser User Role

VORO has an advertising infrastructure.

There is NO separate Advertiser user category in V0.0.1.

---

7. OFFICIAL 14-PHASE ROADMAP

---

PHASE 01 — FOUNDATION

Build and establish the technical foundation.

Requirements:

- Flutter project foundation
- Android project
- Development environment
- VS Code integration
- Basic application architecture
- Project structure
- Configuration
- Environment variables
- Supabase connection
- Initial backend connection
- Basic application structure
- Reusable components
- Error-handling foundation

Do not rebuild a working foundation unnecessarily.

---

PHASE 02 — VIDEO EXPERIENCE / FEED

VORO must be video-first.

When the application opens:

→ The user should enter the video experience directly.

Requirements:

- Vertical video feed
- Full-screen video experience
- Swipe up → next video
- Continuous video-oriented experience
- Appropriate video playback state handling

There must NOT be an unnecessary landing page.

Navigation rule

Do not use a permanent bottom navigation containing:

- Home
- Discovery
- Search
- Creator
- Profile

These functions may still exist.

They should be accessible contextually.

Example:

Video
→ Avatar / Username
→ User Profile
→ User's Videos

Important:

Do not merely hide the old bottom navigation.

Inspect and restructure:

- Routes
- Navigation
- Deep links
- Back navigation
- State management
- Screen relationships

---

PHASE 03 — SUPABASE BACKEND + VIDEO STORAGE

Implement the backend architecture using:

- Supabase
- PostgreSQL
- Supabase Auth
- Supabase Storage
- RLS

Requirements include:

- Database architecture
- User data
- Video data
- Video metadata
- Storage buckets
- Relationships
- Backend queries
- Validation
- Storage policies
- Backend authorization

Security must not depend on Flutter UI.

Database and storage permissions must be enforced server-side.

---

PHASE 04 — AUTHENTICATION + PROFILE

Implement:

- Registration
- Email/password authentication
- Login
- Logout
- Session persistence
- Authentication state
- Email verification
- User profile
- Username
- Avatar
- User information

Production authentication must use the real VORO production configuration.

Do not use localhost configuration for production authentication or redirects.

Profile must not become a permanent bottom-navigation tab.

---

PHASE 05 — VIDEO INTERACTIONS

Implement persistent video interactions.

Requirements:

- Like
- Unlike
- Comments
- View comments
- Save video
- Remove saved video
- Interaction counts
- User-specific interaction state
- Persistence
- RLS/security
- Authenticated-user handling

Prevent invalid or duplicate records where appropriate.

All interaction data must be stored correctly in the backend.

---

PHASE 06 — VIDEO UPLOAD + PUBLISHING

Critical business rule

Any registered/authenticated user can upload and publish videos.

There is NO requirement:

USER
→ REQUEST CREATOR
→ APPROVED CREATOR
→ UPLOAD

The correct flow is:

REGISTERED USER
→ SELECT VIDEO
→ UPLOAD
→ SUPABASE STORAGE
→ VIDEO METADATA
→ PUBLISH
→ VIDEO FEED

Requirements:

- Video selection
- Upload
- Storage
- Video metadata
- Publishing
- Upload state
- Progress/state handling where appropriate
- Errors
- Validation
- File restrictions
- Secure storage
- Backend authorization

The upload system must integrate with the normal VORO video architecture.

---

PHASE 07 — DISCOVERY + SEARCH

Implement content discovery and search.

Requirements:

- Video/content discovery
- User search
- Video search
- Content search
- Appropriate contextual access

Discovery and Search must remain available as functionality.

They do not need to become permanent bottom-navigation tabs.

---

PHASE 08 — AI VIDEO GENERATION

Implement the architecture for AI-generated video.

Flow includes:

AI GENERATION REQUEST
→ PROCESSING
→ GENERATED VIDEO
→ STORAGE
→ METADATA
→ PUBLISHING

Requirements:

- AI generation request
- Processing state
- Generated video handling
- Storage
- Metadata
- Publishing workflow
- Error handling
- Backend integration

AI-generated videos must use the normal VORO video architecture.

Do not destroy or replace the normal user-upload workflow.

If an external AI provider requires credentials/API access that are not available, do not fabricate credentials or pretend the external service is operational.

Create the correct integration architecture and configuration safely.

---

PHASE 09 — RECOMMENDATION / FEED INTELLIGENCE

Implement recommendation/feed intelligence.

Potential signals include:

- Watch behavior
- Likes
- Saves
- Comments
- User interaction
- Video performance
- Content relevance

The recommendation system should use available VORO data appropriately.

Do not unnecessarily replace the existing feed architecture.

Inspect the current implementation before making major architectural changes.

---

PHASE 10 — ADMIN / PLATFORM MANAGEMENT

Implement platform administration.

Potential areas:

- User management
- User review
- User blocking
- Content management
- Content removal
- Reports
- Platform management
- Notifications where approved
- Settings
- Monitoring
- Revenue monitoring
- Advertising monitoring

Critical security rule

Never hard-code administrator authority in Flutter.

Never use:

- Hard-coded owner email
- Hard-coded username
- Hard-coded password
- Hard-coded admin secret
- Client-side-only admin checks

Correct model:

USER AUTH
→ SUPABASE
→ ROLE / PERMISSION
→ RLS / BACKEND AUTHORIZATION
→ ADMIN OPERATION

Flutter is only the interface.

Backend systems determine authority.

---

PHASE 11 — COMMUNITY + SAFETY + MODERATION

Implement platform safety and moderation.

Requirements:

- User reports
- Video reports
- Blocking
- Content moderation
- Content removal
- Abuse prevention
- Moderation states
- Admin review
- Backend enforcement
- Security rules
- Server-side security

Moderation authority must not rely solely on the mobile application.

---

PHASE 12 — MONETIZATION + REVENUE FOUNDATION

VORO's monetization model is based on advertising revenue.

The platform must not finance creator/user payouts from the owner's personal money.

The intended financial flow is:

ADVERTISING REVENUE
→ REVENUE CALCULATION
→ VORO SHARE
→ ELIGIBLE CREATOR / USER SHARE
→ LEDGER

Requirements:

- Revenue records
- Revenue ledger
- Earnings
- Monetization eligibility
- Revenue attribution
- Platform share
- User/creator share
- Transactions
- Secure financial data
- Administrative financial monitoring

Important

Uploading a video does NOT require Creator status.

A normal registered user can upload and publish.

Monetization eligibility is a separate concept and must not be confused with upload permission.

Do not invent additional monetization requirements without owner approval.

---

PHASE 13 — ADVERTISING SYSTEM

Implement the VORO advertising infrastructure.

Requirements:

- Advertisement records
- Campaign information
- Ad placement
- Ad delivery
- Impression tracking
- Click/engagement tracking where appropriate
- Revenue tracking
- Reporting
- Administrative controls
- Connection to revenue ledger

Critical rule

There is NO Advertiser user role in V0.0.1.

Do NOT implement:

USER
→ ADVERTISER ACCOUNT

Advertising campaigns and advertising management are platform/backend concepts.

---

PHASE 14 — PRODUCTION + GOOGLE PLAY

Prepare VORO for real production.

Requirements:

Production

- Production configuration
- Supabase production configuration
- Database verification
- Storage verification
- Authentication configuration
- Production redirect URLs
- Environment variables
- RLS verification
- Storage policy verification

Android

- App signing
- Release configuration
- Android release build
- Physical-device testing

Testing

Test:

- Registration
- Login
- Email verification
- Session persistence
- Video feed
- Video playback
- Swipe behavior
- Profile
- Video upload
- Video publishing
- Supabase
- Storage
- Interactions
- Search
- Discovery
- Admin functions
- Moderation
- Advertising
- Revenue systems
- Network failures
- Weak network conditions
- Stability
- Performance
- Crash/error handling
- Security

Before production:

- Remove localhost production dependencies
- Remove development/debug functionality where inappropriate
- Remove test/dev data
- Verify authentication
- Verify upload
- Verify playback
- Verify profiles
- Verify interactions
- Verify RLS
- Verify administration
- Verify moderation
- Verify advertising
- Verify revenue
- Verify application stability

The application must be tested on a real Android phone before Google Play release.

---

8. DATABASE SECURITY

Review and implement:

- Database RLS
- Storage policies
- Insert policies
- Update policies
- Delete policies
- Ownership policies
- Video ownership
- User permissions
- Admin permissions
- Moderation permissions
- Financial permissions

Never expose:

- Supabase service-role key
- Backend secrets
- Private credentials
- AI provider secrets
- Administrative secrets

inside the mobile application.

---

9. STORAGE SECURITY

Video storage must use secure Supabase Storage policies.

The system must verify:

- Who can upload
- Who owns a video
- Who can update metadata
- Who can delete
- Who can publish
- Who can access protected resources

Storage security must be enforced by backend/storage policies.

---

10. DEVELOPMENT PROCEDURE

Before modifying the project, inspect:

1. Project structure
2. Flutter files
3. Routes/navigation
4. Screens
5. Widgets
6. Supabase configuration
7. Database schema
8. RLS
9. Storage buckets
10. Storage policies
11. Authentication
12. Upload system
13. Feed
14. Profile
15. Admin
16. Advertising
17. Financial/ledger systems

Do not assume something is missing without checking.

Do not rewrite functioning code unnecessarily.

---

11. MAJOR CHANGE PROCEDURE

For every major architectural change:

1. Identify the current implementation.
2. Identify dependencies.
3. Identify affected Flutter files.
4. Identify affected Supabase tables.
5. Identify affected RLS policies.
6. Identify affected Storage policies.
7. Identify affected backend functions.
8. Create an implementation plan.
9. Implement.
10. Test.
11. Fix errors.
12. Report exact changes.

Large destructive changes require explicit owner approval.

---

12. QUALITY CONTROL

The AI development agent must:

- Inspect before modifying.
- Implement actual functionality.
- Avoid fake/mock implementations unless explicitly required for development.
- Run tests where available.
- Run Flutter analysis.
- Fix compilation errors.
- Fix runtime errors discovered during testing.
- Verify Supabase integration.
- Verify RLS.
- Verify Storage policies.
- Verify authentication.
- Verify navigation.
- Verify video playback.
- Verify upload/publishing.
- Verify backend security.

Never report success merely because files were created.

A phase is complete only when its functionality is actually implemented and verified.

---

13. GIT / VERSION CONTROL

GitHub is the source repository for the VORO codebase.

Use version control properly.

Recommended structure:

- One meaningful change per commit where practical.
- Do not overwrite working functionality without a recoverable commit.
- Keep database migrations versioned.
- Keep configuration structure documented.
- Do not commit secrets.
- Do not commit API keys.
- Do not commit service-role credentials.

---

14. ENVIRONMENT VARIABLES

Sensitive configuration must use environment variables or secure configuration.

Never commit secrets directly into source code.

Examples of sensitive values include:

- Supabase credentials
- AI provider API keys
- Backend secrets
- Administrative secrets

Production and development environments must be separated appropriately.

---

15. CURRENT NAVIGATION MODEL

The official VORO navigation concept is:

APP OPEN
→ VIDEO FEED

Video interaction:

VIDEO
→ AVATAR / USERNAME
→ PROFILE
→ USER VIDEOS

Do not restore a permanent bottom navigation simply because older versions of the application used one.

Features such as Search and Discovery can remain accessible through contextual UI.

---

16. OFFICIAL BUSINESS MODEL

VORO is designed around a video platform monetization model.

Advertising generates platform revenue.

Revenue is calculated and recorded.

A portion belongs to VORO.

An eligible portion can be attributed to eligible creators/users according to the monetization system.

Financial records must be represented through reliable backend records and ledger architecture.

The owner must not personally finance creator payouts.

---

17. IMPLEMENTATION ORDER

The official implementation order is:

01 Foundation
↓
02 Video Experience / Feed
↓
03 Supabase Backend + Storage
↓
04 Authentication + Profile
↓
05 Video Interactions
↓
06 Video Upload + Publishing
↓
07 Discovery + Search
↓
08 AI Video Generation
↓
09 Recommendation / Feed Intelligence
↓
10 Admin / Platform Management
↓
11 Community + Safety + Moderation
↓
12 Monetization + Revenue Foundation
↓
13 Advertising System
↓
14 Production + Google Play

Dependencies must be respected.

Do not skip foundational dependencies simply to make the UI appear complete.

---

18. AGENT BEHAVIOR

The development agent must act as:

- Senior Software Architect
- Full-Stack Engineer
- Flutter Engineer
- Backend Engineer
- Supabase Engineer
- PostgreSQL Engineer
- Security Engineer
- Code Reviewer
- QA Engineer

The agent must prioritize:

1. Correct architecture
2. Security
3. Real functionality
4. Maintainability
5. Scalability
6. Testing
7. Clean implementation

Do not prioritize visual appearance over functional architecture.

---

19. ABSOLUTE PROHIBITIONS

The agent must NOT:

- Create a new roadmap.
- Add phases beyond 14.
- Mix V0.0.1 with V0.0.2.
- Mix V0.0.1 with V0.0.3.
- Require Creator status for uploading.
- Create an Advertiser user role.
- Hard-code admin authority.
- Put service-role secrets in Flutter.
- Use localhost for production.
- Treat hidden UI as security.
- Delete working functionality merely because navigation changes.
- Perform an unnecessary complete rewrite.
- Invent missing business rules.
- Fabricate external API credentials.
- Claim unfinished work is complete.
- Replace Flutter/Android with a different application architecture without owner approval.

---

20. FINAL PROJECT OBJECTIVE

At the end of VORO V0.0.1, the project must be a real, functional, secure Flutter Android video platform containing the complete approved 14-phase foundation.

The final application must be capable of:

- User registration
- Authentication
- Profiles
- Video-first feed
- Video playback
- Swipe navigation
- Likes
- Comments
- Saves
- Video upload
- Video publishing
- Discovery
- Search
- AI video generation architecture
- Recommendation/feed intelligence
- Administration
- Moderation
- Monetization/revenue foundation
- Advertising infrastructure
- Secure Supabase backend
- RLS
- Storage policies
- Production Android build
- Physical-device testing
- Google Play preparation

The implementation must remain faithful to the official VORO V0.0.1 architecture and business rules.

VORO V0.0.1 — 14 PHASES — OFFICIAL SOURCE OF TRUTH
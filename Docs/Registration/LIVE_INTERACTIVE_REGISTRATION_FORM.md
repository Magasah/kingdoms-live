# TikTok LIVE Interactive Games — copy-ready answers
GAME NAME:
KINGDOMS LIVE

DEVELOPER / PROJECT:
KINGDOMS LIVE

LEGAL OPERATOR (if requested):
[OPERATOR LEGAL NAME REQUIRED]

CONTACT EMAIL:
kingdomslive.game@gmail.com

COUNTRY:
Tajikistan

PLATFORM:
Windows PC / Desktop

GENRE:
Interactive Strategy / LIVE Interactive Battle

STATUS:
Functional / Preparing for authorized LIVE integration

WEBSITE:
https://magasah.github.io/kingdoms-live/

GAME INTRODUCTION:
KINGDOMS LIVE is a real-time RED vs BLUE interactive battle game for Windows and LIVE streaming. Viewers will be able to influence an ongoing automated kingdom battle through supported LIVE interactions when authorized integration is available. Authorized Gift events can trigger gameplay actions such as summoning Warriors, Archers, Mages, Knights, Heroes and Dragons. Viewer-associated units display the viewer's username and automatically fight opposing forces before advancing toward the enemy castle. The functional local game and simulator demonstrate this flow; production TikTok LIVE transport/access is awaiting authorization.

INTERACTION FLOW:
Authorized LIVE Event -> TikTokLiveProvider -> NormalizedLiveEvent -> LiveEventRouter -> GiftCatalog / GiftActionResolver -> TeamResolver -> SpawnManager -> ViewerUnitData -> Gameplay.
The provider uses an authorized transport and schema adapter. GameBootstrap hands events to the main thread. GiftCatalog is the Resources asset backed by GiftActionCatalog; production mappings resolve through LiveGiftMappings. SpawnManager creates ViewerUnitData before passing it to BattleSimulation.
Technical details and retention: DATA_FLOW.md.

VIEWER EXPERIENCE:
Supported events summon viewer-associated fighters or a Dragon sequence. Teams persist for the running game session. Battles run across three lanes with automatic rounds, castle health, unit combat and stream-facing announcements. A Russian operator panel supports setup and local testing.

GIFTS AND MONETIZATION:
Gifts and payments are controlled by the streaming platform. KINGDOMS LIVE does not sell units directly to viewers, handle Gift payments or promise cash, prizes, refunds, gambling outcomes or financial returns.

INTEGRATION STATUS:
Local simulator: working. Authorized production TikTok LIVE transport: awaiting access/approval.
No official partnership or approval is claimed. No products or scopes are requested beyond those officially required for an authorized integration.

PRIVACY:
https://magasah.github.io/kingdoms-live/privacy.html
TERMS:
https://magasah.github.io/kingdoms-live/terms.html
CONTACT:
https://magasah.github.io/kingdoms-live/contact.html

DEMO:
Seven existing screenshots are in Media/Review/. Demo video is not yet recorded; use DEMO_VIDEO_SCRIPT.md.
Label simulator footage clearly. Do not represent it as a live production connection.

SUBMISSION:
Prepared answers only; not submitted. Supply the operator's legal name when the actual form requires it, verify the URL, and attach the requested demo.

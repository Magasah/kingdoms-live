# Gift system overview
Gift → Authorized LIVE Event → TikTokLiveProvider → provider schema adapter → NormalizedLiveEvent →
LiveEventRouter / deduplication → GiftCatalog / GiftActionResolver → existing SpawnManager → gameplay.

Development actions: Warrior, Archer, Mage, Knight, Hero, Dragon sequence.
ViewerUnitData preserves the supplied Unicode username, stable user ID, team and source event details.
Viewer/team membership persists for the game session, including round changes.
Real provider Gift IDs will only be configured from authorized provider data.

LocalSimulatorProvider remains available for development. LiveFixture is a separate synthetic replay source
and must never be described as a production gift stream. Fixture mappings cannot resolve production events.

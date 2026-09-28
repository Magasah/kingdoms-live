# KINGDOMS LIVE data flow
Status: functional local simulation; no production LIVE transport is bundled or authorized yet.

## Source and fields
An authorized IAuthorizedLiveTransport and IProviderEventSchema must supply the provider frame/schema.
TikTokLiveProvider parses it off the Unity thread. Fields include event type/ID/time, viewer ID/name,
Gift ID/name, repeat/combo state, team command and limited metadata. Frames are capped at 16,384
characters; credentials and raw auth headers must be stripped by the adapter. Ordinary comments are
discarded; supported team commands are optional. Likes are aggregate-only; follow/share/join ignored.

## Processing
Authorized LIVE Event -> TikTokLiveProvider -> NormalizedLiveEvent -> GameBootstrap main-thread queue
-> LiveEventRouter -> GiftCatalog / GiftActionResolver -> TeamResolver -> SpawnManager
-> ViewerUnitData -> BattleSimulation / gameplay.
GiftCatalog is the asset loaded through Resources and implemented by GiftActionCatalog.
Production gift resolution uses LiveGiftMappings. Router validates, rate-limits and deduplicates;
SpawnManager constructs ViewerUnitData and supplies it to BattleSimulation. Dragon is a special sequence.

## Temporary storage and deletion
- Incoming queue: up to 1,024 events, dequeued up to 32 per Update.
- Event monitor: latest 20 rows, including viewer name and Gift information.
- Deduplication: latest 8,192 accepted provider/event keys; oldest evicted on capacity.
- Team mapping: in-memory user ID -> team dictionary, for the running application session.
- Team command cooldowns: parser memory, capped at 10,000 IDs; expired entries pruned at capacity.
- ViewerUnitData: username, user ID, source event/Gift, team, power and spawn timestamp, attached to units.
- Last-event/Gift fields remain until replaced or the game closes.
- Round resets and provider reconnects are not a full privacy-session reset. Close the game to end
  the session and release its memory. No permanent viewer profile file is created.
- Processed queue entries leave the queue; selected derived data can remain in the monitor, dedup
  history, units or status fields as described above.

## Persistent storage
Gift mappings contain Gift ID/name, source, action/count and enabled status, not a viewer registry.
Settings/mappings persist until changed/deleted. Provider diagnostics use Logs/live-provider.log
and at most one .1 backup. At the next write after exceeding 512 KiB, the old backup is replaced
and the active file rotates. A last entry may slightly exceed the threshold. This is size-bounded,
not a seven-day policy; an idle file may remain longer. Operator deletion is possible when unneeded.
Call sites use states, generic parse/config errors, reconnect delays and unknown Gift IDs/names.
They do not intentionally log credentials, raw exception payloads, auth headers or viewer lists.
Current logger behavior was tested in isolation: Reports/Registration/retention-check.txt.

## Stream display
Usernames and gameplay announcements may appear in the stream. Recordings, audience copies,
screenshots and support exports are independent copies, not deleted by closing the game.

## Website and email
GitHub Pages processes hosting requests under its own privacy statement. The static site adds no
analytics/account/contact-form backend. Support mail goes to kingdomslive.game@gmail.com.
Hosting/email retention is independent of the game log limit.

## Source files
Assets/_Project/Scripts/Live/LiveTransportBoundary.cs
Assets/_Project/Scripts/Live/TikTokLiveProvider.cs
Assets/_Project/Scripts/Core/GameBootstrap.cs
Assets/_Project/Scripts/Live/LiveEventRouter.cs
Assets/_Project/Scripts/Live/GiftActionCatalog.cs
Assets/_Project/Scripts/Live/LiveIntegrationSession.cs
Assets/_Project/Scripts/Live/LiveGiftMappings.cs
Assets/_Project/Scripts/Live/LiveIntegrationConfig.cs

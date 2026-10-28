---
name: make-an-epk
description: Build an electronic press kit (EPK) or booking page for a DJ, producer, singer, rapper, band or any music artist with the MY EPK tools. Use when someone asks for an EPK, a press kit, a one-sheet or a booking page, pastes their SoundCloud, Spotify or Instagram to build one, or asks how to send their music to promoters and venues.
---

# Make an EPK

MY EPK builds a one-page press kit and hosts it at my-epk.com/<handle>. The `my-epk` MCP server in this plugin
does the work. A promoter gives a press kit about five seconds, so build for that.

## Flow

1. If you do not know them yet, ask for the artist name, what they do (DJ, producer, singer, band...) and their city.
   Then call `create_kit` with what you have (only `displayName` is required).
2. Call `find_profiles` with the name. Show the matches and let the artist pick; never add a profile they have not
   confirmed. For anything they paste (a link or an @handle) call `resolve_link` first.
3. Add the confirmed links with `update_kit`. If they have a Spotify, Apple Music, Deezer or Mixcloud profile, call
   `import_catalog` so the releases appear with artwork.
4. Ask three concrete things for the bio (their sound, rooms or festivals they have played, one milestone). Write one
   bio of 60 to 120 words in the third person and 3 to 4 stats ("120 shows", "since 2018"), then save with `update_kit`.
5. Ask which handle they want (my-epk.com/<handle>) and call `set_handle`. If it is taken, offer the suggestions.
6. Give them the `claimUrl`: they open it on their phone, add photos, sign in and tap Publish.

Ask one or two questions at a time and skip anything the artist does not care about; every field but the name is
optional. When you stop to ask, say the draft is saved.

## Rules

- Keep the `kitToken` from `create_kit` and pass it to every later call. Never show it in your messages.
- You cannot publish. `publish_kit` only reports whether the kit is ready and what still blocks it; say plainly that
  the artist publishes on the site.
- Never invent facts about the artist: no venues, releases, follower counts or quotes that the artist or a tool
  result did not give you. Facts over adjectives, no hype words.
- Photos: `add_photos` takes direct public image links only (JPEG, PNG or WebP). For camera-roll photos, point the
  artist to the claimUrl on their phone.
- Up to 6 links, streaming first, then Instagram and one more. Booking email is the only contact needed.

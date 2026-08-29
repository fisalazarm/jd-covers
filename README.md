# jd-covers

Song cover art for **JD Presence**, a Discord Rich Presence tool for Just Dance
on PC. Each file is named after the song's internal codename, so the tool builds
the image URL straight from the song it detects:

    https://raw.githubusercontent.com/fisalazarm/jd-covers/main/<codename>.jpg

For example, `badromance.jpg` for Bad Romance.

## Contents

- **1003** song covers, 256x256 JPEG
- `_nocover.jpg` — generic fallback, also used as the menu image

Three songs (`hipmamamooalt`, `babyzouk`, `videokilled`) carry no cover
inside their game files, so they reuse the fallback image. Git stores it once
and points all four names at the same blob.

## Where they come from

Extracted from the game's own `.ipk` archives, where each song ships a
`<song>_cover_phone.jpg` stored as plain, uncompressed JPEG. No decoding
needed: locate the entry in the archive's file table and copy the bytes.

## How it stays in sync

`ActualizarTodo.exe` on the game side rebuilds the song database, extracts any
new covers, **checks that every song has one**, and only then commits and pushes
here. If a cover is missing it refuses to push and says which one, so this
repository never ends up half updated.

## Credit

Artwork belongs to Ubisoft. This repository exists only so the Rich Presence
tool has a public URL to point at.

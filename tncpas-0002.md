---
# General Front Matter
title       : TNCPAS-0002 - Edition and Staff ID Numbering

# TNCPAS Front Matter Metadata
ID          : TNCPAS-0002
Topic       : Edition and Staff ID Numbering
CreatedAt   : 2022-08-27T12:34:00
LastUpdated : 2022-08-27T11:52:30Z
Authors     :
    - Natsu Tadama
Status      : Draft
Type        : Standard
Scope       : Global
---

## Abstract

`TNCPAS-0002` describes a scheme to number an edition releases or staff with unique
identifier (ID).

## Motivation

Re-releasing an edition is often to do by several clubs in MyAnimeList.
However, this could be an issue if club organizer wants to list any released
editions into a database such Microsoft Office Excel, etc.

The following ID scheme is aimed to resolve the issue while maintaining very
unique ID based on how The Newbie Club did for last a year.

## Numbering an Edition Release

An edition ID can be formatted as such:

```txt
YYMMX
```

Whereas:

* `YY` &mdash; as last 2 digit of release year.
* `MM` &mdash; as 2 digits of release month, including 0.
* `X` &mdash; as capitalized sequence number in alphabetical format (`A`-`Z`)

## Numbering a Staff Contribution on Specific Edition

A staff ID can be formatted as such:

```txt
YYMMMXEEESSSIII
```

Whereas:

* `YY` &mdash; as last 2 digit of release year.
* `MMM` &mdash; as 3 character month of release name in English.
* `X` &mdash; as capitalized sequence number in alphabetical format (`A`-`Z`)
* `EEE` &mdash; as first 3 characters of edition title/theme
* `SSS` &mdash; as first 3 characters of staff/contributor name
* `III` &mdash; as last 3 digits of external user ID, such Discord or
  MyAnimeList user ID.

## Implementation Sample

### Edition ID

On October 2021, there is 3 edition released:

1. [Fall Edition](https://myanimelist.net/forum/?topicid=1961525). Released on
   October 3, 2021. Thus making the ID `2110A`.
2. [Genshin Impact Edition](https://myanimelist.net/forum/?topicid=1965234).
   Released on October 17, 2021. Thus making the ID `2110B`.
3. [TNC X HNE Halloween Collab Edition](https://myanimelist.net/forum/?topicid=1967957).
   Released on October 28, 2021. Thus making the ID `2110C`.

### Staff Contribution ID

## References

1. [github:theNewbieClub-MAL/cardArchive/CONTRIBUTING.md](https://github.com/theNewbieClub-MAL/cardArchive/blob/main/CONTRIBUTING.md)

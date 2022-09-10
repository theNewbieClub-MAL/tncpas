---
# General Front Matter
title       : TNCPAS-0001 - Metadata Format for Card Edition Forum Post

# TNCPAS Front Matter Metadata
ID          : TNCPAS-0001
Topic       : Metadata Format for Card Edition Forum Post
CreatedAt   : 2022-08-27T10:03:20Z
LastUpdated : 2022-08-27T11:52:30Z
Authors     :
    - Natsu Tadama
Status      : Final
Type        : Standard
Scope       : BBCode
---

## Abstract

`TNCPAS-0001` describes a format for machine to read metadata regarding
current card[<sup>[1]</sup>](#fn1) edition release on MyAnimeList forum post.

## Motivation

As The Newbie Club creates several OSS projects such as generating a forum
thread for card edition release and read forum posts, a standard is required to
avoid any unwanted incompability across the projects.

The metadata format is expected to be implemented in various MyAnimeList clubs
for ease card requests parsing/scraping.

## Metadata Structure

1. A metadata for a card edition release format should be started and ended by
   writing `###` (hashed) block at the first and last line of metadata. The
   metadata should be named as `SCRAPEDATA` or `METADATA` after first hashed
   block.

   > **Note** |
   > Please to use `METADATA` rather `SCRAPEDATA`. `SCRAPEDATA` is legacy and
   > will not be supported in future.

   Example:

   ```haskell
   ###METADATA
   {- content -}
   ###
   ```

2. Metadata content is stated by using the following format:

   ```haskell
   >>>KEY>>Value
   ```

   Whereas `KEY` is case **sensitive** 3-characters name/key that is predefined
   in [## Metadata Keys](#metadata-keys), and `Value` is case **insensitive**
   data value.

   User can create their own custom key as long the key is 3 characters long

3. When a key is an array, semicolon (`;`) is used as data separator in
   between. Semicolon is not needed at the end of array data.

   ```haskell
   >>>ARR>>Val;Val;Val;Val{- ;[...] -}
   ```

   Total amount of values in an array is defined by user.

4. When a data has separate values, use vertical bar (`|`). This method only
   applicable for `LIM` key.

   ```haskell
   >>>LIM>>1|2;4;2;4|5{- ;[...] -}
   ```

   By default, left value on `LIM` is a limit for member, and right for club
   staff.

5. If a value is empty/null, use `0`.

6. If a metadata requires a comment, use `{- ... -}` block

   ```haskell
   >>>KEY>>Value
   {- This is a comment -}
   ```

## Implementation Sample

```haskell
###METADATA
>>>THM>>Genderbend
>>>STF>>Iris;0;0;0;0
>>>MAX>>100
>>>LIM>>3|6;0;0;0;0
>>>AVA>>6;0;0;0;0
###
{- Generated with GitHub:theNewbieClub-MAL/editionThreadGenerator-ps1@v0.2.4 in Powershell on 2022-08-22T04:54:46Z -}
```

## Metadata Keys

| Data Type | Definition                |
| --------: | :------------------------ |
|  `Arr(x)` | Array of `x`              |
|     `Bol` | Boolean (`True`, `False`) |
|     `Int` | Integer/numeral           |
|     `Sin` | String OR Integer         |
|     `Str` | String                    |

|  Key  | Stand As            | Data Type  | Required | Description                                                       |
| :---: | :------------------ | :--------: | :------: | :---------------------------------------------------------------- |
| `AVA` | **Ava**ilable       | `Arr(Int)` |   Yes    | Total cards designed by Contributors/Staff in a release           |
| `CLR` | **C**o**l**o**r**   | `Arr(Str)` |    No    | Font colors used on a thread in Hex format (`#ffffff`)            |
| `LIM` | **Lim**it           | `Arr(Int)` |   Yes    | Maximum cards allowed to request each staff per member/staff      |
| `MAX` | **Max**imum         |   `Int`    |    No    | Maximum requests to accept in one release                         |
| `SID` | **S**taff **ID**    | `Arr(Sin)` |    No    | Card Contributors/Staff ID, see [`TNCPAS-0002`](./tncpas-0002.md) |
| `SLP` | **Sl**i**p**        | `Arr(Boo)` |    No    | State if Contributor/Staff allows slip card usage                 |
| `STF` | **St**a**f**f       | `Arr(Str)` |   Yes    | Card Contributors/Staff Name                                      |
| `TEM` | **T**heme **Em**oji |   `Str`    |    No    | Edition emoji (for visual identifier in forum title)              |
| `THM` | **Th**e**m**e       |   `Str`    |   Yes    | Edition title/theme                                               |
| `TID` | **T**heme **ID**    |   `Sin`    |    No    | Edition ID, see [`TNCPAS-0002`](./tncpas-0002.md)                 |

## Syntax Highlighting Support

Metadata uses `haskell` syntax highlight.

## References

1. <a id="fn1"></a> [The Newbie Club Card Guides and FAQ § 💳 What is a card?](https://github.com/theNewbieClub-MAL/cardfaq/blob/main/i18n/en_US.md#-what-is-a-card)
2. [[CARDS] [CLOSED] 🧬 Genderbend - Forums - MyAnimeList.net](https://myanimelist.net/forum/?topicid=2039596&show=0)

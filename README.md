# sentence-miner-mflash-export

Exports tagged sentences from [MorEnglish Sentence Miner] into an `.mflash`
(v1) deck for [Moribund Flash]: one card per tagged segment — the word or
phrase as the term, its grammar tag as the definition, and every sentence it
was mined from as an example. The same term+tag across sentences merges into
one card.

Mine → tag → study.

## Use

The Sentence Miner app must be running (its loopback API serves the data).

```sh
node export.mjs --out ~/path/to/moribund-flash/decks/sentence-miner.mflash
```

Exports the whole sentence library (FILE ▸ Library in the app); if the
library is empty, exports the currently mined sentence instead.

Or register it in the miner's plugin manager (`plugins.toml`):

```toml
[[plugin]]
name = "Export to Moribund Flash"
command = "node /path/to/export.mjs --out /path/to/decks/sentence-miner.mflash"
description = "Library → .mflash deck, one card per tagged segment"
```

No dependencies; auth token is read from the miner's config dir
automatically (`SENTENCE_MINER_TOKEN` overrides).

## Self-check

```sh
node export.mjs --check
```

[MorEnglish Sentence Miner]: https://github.com/EnglishMoribund/MorEnglish_Sentence_Miner
[Moribund Flash]: https://github.com/MoribundMurdoch

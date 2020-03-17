# LoggedFuSkater
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

LoggedFuSkater is a standard along with set of libraries that provides identical string obfuscation in multiple languages.

## Output
The output will be a three word string with optional(up to eight) hexadecimal byte padding at the end.
For example _IncreasinglyAngryBanana_, or with two bytes of padding _IncreasinglyAngryBanana3D9F_.

## Algorithm
Sha1 is used to hash the input into an array of 20 bytes. The bytes will be split as follows: [0..4] adverb index, [4..8] adjective index, [8..12] noun index, [12..20] padding bytes. The indexes are unsigned 32 bit integers parsed with little endian. The resulting word in each category is index modulo word count. The final result is then AdverbAdjectiveNounPadding where padding is the configured number of bytes(0-8) represented by upper case hexadecimal characters.

### Pseudocode
```
hash_bytes = Sha1(input)

adverb_index = LittleEndian.Uint32(hash_bytes[0..4])
adjective_index = LittleEndian.Uint32(hash_bytes[4..8])
noun_index = LittleEndian.Uint32(hash_bytes[8..12])

padding = hash_bytes[12..(12 + padding_count)]

adverb = adverbs[adverb_index % adverbs.len]
adjective = adjectives[adjective_index % adjectives.len]
noun = nouns[noun_index % nouns.len]

result = adverb + adjective + noun + UppercaseHex(padding)
```

## Versioning
Any change to any list of words is a breaking change and therefore a major version.

### Library Versioning
Since the goal is to provide identical obfuscation across all supported languages the major versions of the libraries should always be the same as the standard version they are implementing.
All libraries on must have at least one release compatible with each major release of the standard.

## Word Selection
All words should be:
 - Safe For Work
 - Non-political
 - Non-religious in a specific sense, 'Holy' is ok, 'Jesus' is not

Avoid using trademarked/copyrighted words. It would most likely be fine but **IF** a word had to be redacted for legal reasons, there would be a breaking change _in every_ major release that included said word.

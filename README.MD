# LoggedFuSkater
LoggedFuSkater is a set of libraries that provides identical string obfuscation in multiple languages.

## Output
The output will be a three word string with optional(up to eight) hexadecimal byte padding at the end.
For example _IncreasinglyAngryBanana_, or with two bytes of padding _IncreasinglyAngryBanana3D9F_.

## Versioning
Any change to any list of words is a breaking change and therefore a major version. Since the goal is to provide identical obfuscation across all supported languages the major versions of the language specific libraries should always be the same as the core version they are implementing.

All language libraries on must have at least one release compatible with each major release of the core repository.

## Word Selection
All words should be:
 - Safe For Work
 - Non-political
 - Non-religious in a specific sense, 'Holy' is ok, 'Jesus' is not

Avoid using trademarked/copyrighted words. It would most likely be fine but **IF** a word had to be redacted for legal reasons, there would be a breaking change _in every_ major release that included said word.

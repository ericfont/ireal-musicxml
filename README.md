# ireal-musicxml

iReal Pro to MusicXML converter

[![Build Status](https://travis-ci.org/infojunkie/ireal-musicxml.svg?branch=main)](https://travis-ci.org/infojunkie/ireal-musicxml)

# Usage

```
import * as iReal2MusicXML from 'ireal-musicxml'
const ireal = // Content of HTML file generated by iReal Pro or irealb:// URI
const playlist = iReal2MusicXML.convert(ireal)
// => {
//   name:              // Playlist name
//   songs: [{
//     title:           // Title
//     composer:        // Composer
//     style:           // Song style for display
//     groove:          // Song style for playback
//     key:             // Key signature
//     transpose:       // Transposition in semitones
//     bpm:             // Beats per minute
//     repeats:         // Repeat count
//     music:           // Raw song encoding
//     cells: [ Cell ]  // Array of parsed cells
//     musicXml:        // MusicXML output
//   }]
// }
```

# Development

`xmllint` is required to run tests (but NOT at runtime). Tests are used to ensure that the generated MusicXML is valid.

```
npm install
npm run test
```

# Documentation
- More information [about the iReal Pro format](doc/ireal.md).
- More information [about the MusicXML format](http://usermanuals.musicxml.com/MusicXML/MusicXML.htm).

# Known issues
- No chord (N.C.) MusicXML spec [needs a `root/root-step`](https://forums.makemusic.com/viewtopic.php?f=12&t=2476#p9099), which [confuses MuseScore](https://musescore.org/en/node/313008).
- Generating a staff note for each chord [confuses MuseScore into playing that (dummy) note](https://musescore.org/en/node/313008), which is only there to indicate the rhythm structure. Currently exporting a rest instead.

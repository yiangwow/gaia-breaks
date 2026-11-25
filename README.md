# gaia-breaks: Born to be a star

A WebGL piece set to one track. It does not react to the audio. Every moment is
choreographed by hand, so it plays the same every time.

It has four movements: Dead World, Fallen Titan, The Maw, The Gate. It is a story
of struggle. 七転び八起き: fall seven times, get up eight.

It looks like a game screen that is breaking. There is a wide scene, a HUD drawn
on top of it, and glitches that grow with the music. On a few chosen beats the
picture flips to a wireframe view. At the end it goes quiet.

## Run

```bash
npm install
npm run dev      # dev server with a time scrubber, at localhost:5173
npm test         # logic tests
npm run build    # one self-contained dist/index.html
```

The build puts everything (code, shaders, audio) into `dist/index.html`. You can
open that file or send it to someone. It needs no server.

## How it works

- The audio's current time is the only clock.
- `src/score-data.js` holds the keyframes. `src/score.js` turns a time into what
  to show: which movement, how much corruption, which HUD parts, wireframe on or off.
- Each frame draws the outgoing and incoming movement into two textures.
  `corruption.frag` mixes them and glitches the result. `ui/uiLayer.js` draws the
  HUD on top.
- The scenes are plain WebGL2 fragment shaders. There are no meshes and no libraries.

## Note

The track is not in this repository. To run it, put an audio file at
`audio/born-to-be-a-star.mp3`.

Music Finder

I built this because I kept hearing songs in cafes/stores and had no idea what they were.It's basically a lightweight Shazam clone you hit record,it listens for a few seconds and tells you the song and artist.

Languages used : 

HTML       — page structure, all the buttons/text/layout.
CSS        — styling, colors, the spinning record animation.
JavaScript — everything that actually happens: recording audio,sending it off to get identified, showing the result.

No frameworks, no build tools,no npm install. Just one file,opened straight in the browser.

How it works, roughly :

The whole thing runs in three stages:

1. Recording When you hit the button, the browser asks for mic permission (getUserMedia),then a MediaRecorder captures about 6 seconds of audio.That audio gets collected into small chunks as it records,then glued together into one file once it stops.

2. Sending it off That recorded clip gets packaged up and sent to AudD(a free audio recognition API)using fetch.AudD does the actual hard part,matching the clip against a huge database of songs,and sends back the title,artist,and album art if it finds a match.

3. Showing the result The page just takes whatever AudD sends back and drops it into the page,updating the song title,artist name,and pulling in the cover art image.If nothing matches,it shows an error message instead of breaking.

There's also a small history list that keeps the last few songs you've found during that session(resets on refresh, nothing's saved permanently).

How to use it :

You'll need a free API key from audd.io first. Once you have that:

Open index.html in your browser
Paste the key in when it asks
Hit the record button near whatever's playing
Give it a few seconds and it'll show you the title, artist and cover art

Works better if you're close to the speaker and there's not a ton of background noise. If it doesn't recognize something, just try again — sometimes a slightly different clip catches it.

Your key only lives in the browser tab while it's open, it's not saved anywhere, so you'll need to paste it back in if you refresh.

No install needed, just open the file. That's it.

# Car Karaoke: setup (about 10 minutes)

One file, `index.html`. No server, no build step.

## 1. Host it on GitHub Pages
1. Create a repo (e.g. `lyrics`) on your PERSONAL account 
2. Upload `index.html`, then Settings > Pages > deploy from `main` / root.
3. Your URL will be `https://eitanshay.github.io/lyrics/` (keep the trailing slash).

## 2. Create the Spotify app
1. https://developer.spotify.com/dashboard > Create app.
2. Redirect URI: exactly `https://eitanshay.github.io/lyrics/`
3. Check "Web API". Save.
4. Settings > User Management: add your own Spotify email.
5. Copy the Client ID and paste it into `const CLIENT_ID = ""` at the top of `index.html`, then commit. (Typing it on the car screen is miserable, so bake it in. A PKCE client ID is public by design.)

Since Feb 2026, new Development Mode apps require the app OWNER to have Spotify Premium and are capped at 5 users.

## 3. In the Tesla
Open the browser, go to your URL, tap Connect Spotify, log in once. Start music in the car's Spotify app. The token is stored in the browser and refreshes itself.

## Controls
Tap the screen to show the buttons. "Lyrics earlier/later" shifts sync in 0.5s steps (saved). Tapping any lyric line snaps sync so that line is "now". A+/A- changes size.

## Known limits
- Lyrics come from LRCLIB (community-made, free, line-level timing). Highlighting inside a line is estimated, not real word timing. Obscure or new tracks may have none.
- The page follows your Spotify ACCOUNT state. Private Session or a car that is not signed into your account will show "Nothing playing".
- Tesla restricts the browser while the car is in Drive on many builds. Test in Park first.

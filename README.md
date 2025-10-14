<img width="860" height="293" alt="image" src="https://github.com/user-attachments/assets/d5e055a2-2534-4a7a-8d33-8e02fb10c3e6" />

# BlueSwiftHammer
A (future) self‑hostable tool to automatically block Bluesky users who subscribe to specified lists.  
Run it yourself, keep your blocklists in sync, no hosted service required.

### What it’s supposed to do
- You give it the URL of one or more blocklists.
- It creates a blocklist under your account for each list you want to track.
- It looks at everyone who has subscribed to that list.
- If they’ve chosen “block” (instead of “mute”), it adds them to your blocklist (if that distinction is exposed/possible).
- It keeps checking every so often (default: 20 minutes) so new subscribers get caught too.
- It runs in the background on a computer or server you control. Maybe as a systemd process? Real

That’s the goal: no dashboards, no hosted service. Not magic,  *a r t i f i c i n g!*
  A script for you to run on your own machine or server.

### Current status
This is just documentation and a starting point. First milestone is a simple Python script with a config file; Docker support may come later.

### Roadmap
- [ ] Basic Python script that logs in with an app password and blocks list subscribers
- [ ] Config file for handle, password, list URI, and sync interval
- [ ] Local cache so it doesn’t re‑block the same people every run
- [ ] Dockerfile for people who don’t want to mess with Python installs
- [ ] Logging / audit trail so you can see what it did

### Safety notes
- Use an app password, not your main Bluesky password.
- Local config file?
- Local encryption?
- This tool will actually block people from your account. Double‑check the list you’re syncing before you run it.
- If you want to reset, just delete the local cache/config file.

### License
[CC0 1.0 Universal (Public Domain Dedication)](https://creativecommons.org/publicdomain/zero/1.0/)

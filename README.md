<img width="860" height="293" alt="image" src="https://github.com/user-attachments/assets/d5e055a2-2534-4a7a-8d33-8e02fb10c3e6" />

# BlueSwiftHammer
A (future) self‑hostable command-line tool to automatically block Bluesky users who subscribe to specified lists.  
Run it yourself, keep your blocklists in sync, no hosted service required.

### Why does this exist?
To protect yourself from people who abuse blocklists to harass others by blocking specific list creators and their subscribers & personally reduce your attack surface because you can gather a lot about a person from the blocklists they subscribe to.

### What it’s supposed to do
- It's a command-line tool to manage a config file, and a scheduled task/automated tool that uses the config file to manage reflective/responsive blocklists.
- You give it the URL of one or more blocklists, and some preferences ("nuclear" or "normal" block option, for example)
- It looks at each account who has subscribed to each list, and adds them to a corresponding list (allowing you to block the list manager/creator and all subscribers).
  - Nuclear: does not remove  users after they've unsubscribed from the target list.
  - Normal: Compares the current subscribers of the target list to the mirror/cache and removes them from the reflected list when they unsubscribe. (default)
- It should create a new list for each target list, never merging them together.
- The service keeps checking every so often (default: 30 minutes?) so new subscribers get caught too, and merged into the right lists.
- Individual accounts can be exempted from blocklists globally in the config file.
- It runs in the background on a computer or server you control. Systemd or something on linux, scheduled task on windows?

# That’s the goal: no dashboards, no hosted service. 
  Not magic,  *a r t i f i c i n g!*
  A script for you to run on your own machine or server and config file manager to help keep things from getting too stupid.

### Current status
This is just documentation and a starting point. First milestone is a simple Python script with a config file; Docker support may come later.

### Roadmap
- [ ] Basic Python script that logs in with an app password and blocks list subscribers
- [ ] Config file for handle, password, list URI, and sync interval
- [ ] Local cache so it doesn’t re‑block the same people every run
- [ ] Dockerfile for people who don’t want to mess with Python installs
- [ ] Logging / audit trail so you can see what it did

### Safety/Implementation Questions/Notes
- Use an app password, not your main Bluesky password.
- Local config file?
- Local encryption?
- Rate Limits?

### User Safety Notes
- How do we stop people from hurting each other with this tool or do we have to accept that people are terrible?
- This tool will actually block people from your account. Double‑check the list you’re syncing before you run it.
- If you want to reset, just delete the local cache/config file and the blocklists on your account.

### License
[CC0 1.0 Universal (Public Domain Dedication)](https://creativecommons.org/publicdomain/zero/1.0/)

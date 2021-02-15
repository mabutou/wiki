---
description: 'http://www.alecjacobson.com/weblog/?p=2783'
---

# Kill Apple Remote Desktop via ssh

I tried to remote control my work machine from home using Apple Remote Desktop and got the following error:

```text

Apple Remote Desktop or another administration application is currently running.
```

The problem was that I had left the same Apple Remote Desktop client running on my work machine. To solve this I `ssh`ed to that machine and issued:

```text

killall "Remote Desktop"
```

**Update:** You can then use remote desktop to reopen the Apple Remote Desktop client and go to preferences &gt; Security and check “Allow control of this computer when this application is running”


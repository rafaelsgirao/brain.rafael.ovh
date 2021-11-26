
# Welcome to Dendron

### Nº1
Answer's in Slack.

### Nº2
This is simple. All you need to do is create a python requests session object and use it to start the game on `/hello` . After that, keep hitting the `/more` endpoint until you either reach the number you want, in which case just hit the `/finish` endpoint once to get the flag, or create a new requests `Session` object and start over. Repeat until flag is achieved.

### Nº 3
Same base as nº2, but now there's a `remaining_tries` cookie set to 1. 
Simply set this cookie on the `Session` object to something high enough
to be able to hit the `/more` endpoint enough times.


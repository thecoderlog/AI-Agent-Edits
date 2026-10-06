# How an AI coding agent actually edits your code — demo

The demo from the video: a small React app, and a see-through coding agent that edits it.

- `src/UserCard.jsx` is the file the agent changes ("add a loading skeleton to the user card").
- `src/UserCard.test.jsx` is what the agent runs to check its work (`npm test`).
- `agent/mini-agent.mjs` is the agent: a model in a loop with three tools (`read_file`, `edit_file`, `run_command`), printing every round raw. Each run is also saved to `agent/runs/<name>.json`.

```sh
npm install
cp .env.example .env        # put your ANTHROPIC_API_KEY in it
npm run dev                 # the app, http://localhost:5173
npm test                    # the one test file
npm run agent -- "add a loading skeleton to the user card"
npm run agent -- --break "add a loading skeleton to the user card"   # changes a line behind the model's back
git checkout -- src/UserCard.jsx   # undo
```

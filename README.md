# Zeralyx model facts

API prices and facts for the models Zeralyx offers through Claude Code, Codex and Grok Build, taken from each company's
own pages (Anthropic, OpenAI, xAI) and checked every 15 minutes. Zeralyx shows them when you pick a model.

Prices are the companies' API rates in USD per million tokens. They are not the cost of a Claude, ChatGPT or Grok plan.

## Files

- `facts-v2.json`: the facts, signed by the watcher's key, with each model's Fast price where the company sells Fast.
- `facts-v1.json`: the same facts without Fast prices, for Zeralyx releases from before them.
- `keys-v1.json`: which watcher keys may sign facts, and which were revoked, signed by a master key that never leaves
  its owner's PC. Zeralyx pins the master public keys in its code.

Each file is `{"keyId", "payload", "signature"}`: `payload` is the base64 JSON document, and `signature` is Ed25519 over
the UTF-8 line `Zeralyx model facts v2` (`Zeralyx model facts v1` for facts-v1.json, `Zeralyx model facts keys v1` for
the keys file) and a newline, followed by the payload bytes. Zeralyx rejects a file with an unknown field, an
out-of-range number, a lower sequence or a key that is not approved or was revoked, and keeps its last verified copy.
The files are display data only: nothing in them is run, opened or installed.

There are no workflows in this repository.

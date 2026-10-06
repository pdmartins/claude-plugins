# pdmartins plugins for Claude Code

This repository is the `pdmartins` plugin marketplace: a catalog that tells
Claude Code where each plugin lives. The plugins themselves live in their own
repositories, and each one carries its own version.

## Plugins

| Plugin | What it does | Repository |
|---|---|---|
| `rules-by-trigger` | Path-scoped rules: markdown rules injected into context the moment Claude touches a file matching a glob, or loads a named skill. A scalable replacement for nested CLAUDE.md files. | [pdmartins/rules-by-trigger](https://github.com/pdmartins/rules-by-trigger) (folder `plugin`) |
| `chat-frames` | Frames each prompt and each reply in the transcript, with a timestamped top rule and a closing rule. | [pdmartins/chat-frames](https://github.com/pdmartins/chat-frames) (folder `plugin`) |

## Install

Inside Claude Code, add the marketplace once, then install the plugins you want:

```
/plugin marketplace add pdmartins/claude-plugins
/plugin install rules-by-trigger@pdmartins
/plugin install chat-frames@pdmartins
```

The same from a shell:

```bash
claude plugin marketplace add pdmartins/claude-plugins
claude plugin install rules-by-trigger@pdmartins
claude plugin install chat-frames@pdmartins
```

Inside Claude Code, `/plugin install` opens the plugin's details in the
`/plugin` panel, where you confirm the install. A plugin installed in a running
session takes effect after `/reload-plugins`.

To refresh the catalog later:

```
/plugin marketplace update pdmartins
```

## License

[MIT](LICENSE)

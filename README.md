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

## Moving from the old marketplace

The `pdmartins` marketplace used to live in
[pdmartins/rules-by-trigger](https://github.com/pdmartins/rules-by-trigger).
If you added it from there, move to this repository. The marketplace name and
the install names stay the same.

Claude Code registers one marketplace per name, so remove the old one first:

```
/plugin marketplace remove pdmartins
/plugin marketplace add pdmartins/claude-plugins
/plugin install rules-by-trigger@pdmartins
/reload-plugins
```

Removing the marketplace also uninstalls the plugins you installed from it, so
`rules-by-trigger` goes away with the first line and comes back with the third.
Your rules are not touched: they live in `~/.claude/rules-by-trigger/` and in
each project's `.claude/rules-by-trigger/`, outside the plugin. The plugin's
data directory does go: it holds which rules each session already received, so
a session that was open during the move may get a rule injected once more.

If a settings file (`~/.claude/settings.json` or a project's
`.claude/settings.json`) declares `pdmartins` under `extraKnownMarketplaces`,
change its source there too. Claude Code fetches the marketplace again when its
source changes in settings:

```json
"extraKnownMarketplaces": {
  "pdmartins": {
    "source": { "source": "github", "repo": "pdmartins/claude-plugins" }
  }
}
```

To check the move, run `/plugin marketplace list`: `pdmartins` should point at
`pdmartins/claude-plugins`.

## License

[MIT](LICENSE)

# Repository rules

- Every text published from this repository (README files, translations, SKILL.md, plugin metadata, and the planned docs/ site) goes through careful revision with the readers-ear skill before it is committed: a read by a fresh context and a reference check, as SKILL.md describes. When revising a translation, never use another translation, or the English source, as a phrasing reference; compare only against text originally written in that language.
- The English files are authoritative. When `plugin/skills/readers-ear/SKILL.md` or `README.md` changes, update the files in `translations/` in the same commit, including the date at the top of each `SKILL.<lang>.md`.
- Don't put anyone's real name in published files or commit metadata. Use `Motestream <motestream.studio@gmail.com>` as the author name and email.
- Keep `plugin/` limited to what users install. The planned docs/ site and the translations stay outside it.
- Names: the plugin, marketplace, and skill are all `readers-ear`, and the GitHub path is `motestream/readers-ear`. If any of these changes, replace it everywhere at once (plugin.json, marketplace.json, SKILL.md frontmatter and folder name, all READMEs and translations).

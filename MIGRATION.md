# Editor support for the PlayerBot migration

This is the owner fork `joshhmann/aa-editor`, alongside
[joshhmann/AAEmu-1.2-Rust](https://github.com/joshhmann/AAEmu-1.2-Rust) and
[joshhmann/AABevy1.2](https://github.com/joshhmann/AABevy1.2).
Publish feature branches only to this fork. Upstream is intake-only; do not
push or open upstream PRs or send messages without the owner asking.

The engine dependency URLs now point to the owned client fork. Their exact
revision remains `17d6258a1bca978c61830354b9e9832d08f0eea8`, preserved on
`compat/editor-engine-17d6258a`; no engine source/API upgrade is implied.
The current community client's main history is separate, so changing that pin
to its latest commit is a later compatibility task.

The first server migration checkpoint verifies native scripted login/game and
selected state across a cold Game restart. It does not verify this editor's
rendering, new navigation traversal or live PlayerBot inspection.

Use the existing editor for world/content inspection and specifically approved
content authoring. Future bot inspection should be read-only and show actual
server state, goal, target, request/refusal and route knowledge. NPC FollowPath
files and bot atlas/road graph data remain separate formats.

Reference SQLite content changes require approval of a concrete patch on a
working copy with recorded hashes and matched client/server data. Use
`--read-only-db` for investigation. Bot progress stays in MySQL. F5 preview and
fake UI data do not prove server AI, quests or autonomous behavior.

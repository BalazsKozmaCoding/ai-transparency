# AI transparency for documents

<sub>(**[AI transparency](README.md):** proposed by <img src="badges/human.svg" alt="human" align="absmiddle"> · drafted by <img src="badges/ai.svg" alt="AI" align="absmiddle"> · reviewed by <img src="badges/human.svg" alt="human" align="absmiddle"> · approved by <img src="badges/human.svg" alt="human" align="absmiddle"> at `f3ebd36`)</sub>

In projects where documents are written with AI, this short line under a document's title tells you how much a person was involved in its creation, so you know what you are reading.

## How to read the line (for humans)

The line at the top of this page is an example. Its parts:

- **proposed by**: whose idea the document was.
- **drafted by**: who wrote the text.
- **reviewed by**: who read it and commented.
- **approved by**: a person read the whole document and was happy with it. The short code after it (for example `a1b2c3d`) names the version they read. The document may have changed since; to see how, compare it with that version in git.

A blue <img src="badges/human.svg" alt="human" align="absmiddle"> box marks a step a person did, a purple <img src="badges/ai.svg" alt="AI" align="absmiddle"> box a step an AI did. A dash, —, means the step has not happened yet.

One more form: **all AI, not reviewed by a human** means no person took part. Read it as an AI's notes, for example a worklog.

## Writing the line (for AI agents)

The rest of this page is for agents that write documents in a repository that uses the line (and for a person who edits the line by hand). Every document there (for example the README and the files in `docs/`) starts with the line, directly under the title. It is set in smaller text and in parentheses, so that it reads as a note about the document and not as part of its content, and its label links to this page.

### The line

```markdown
<sub>(**[AI transparency](README.md):** proposed by <img src="badges/human.svg" alt="human" align="absmiddle"> · drafted by <img src="badges/ai.svg" alt="AI" align="absmiddle"> · reviewed by <img src="badges/human.svg" alt="human" align="absmiddle"> · approved by <img src="badges/human.svg" alt="human" align="absmiddle"> at `a1b2c3d`)</sub>
```

It renders as:

<sub>(**[AI transparency](README.md):** proposed by <img src="badges/human.svg" alt="human" align="absmiddle"> · drafted by <img src="badges/ai.svg" alt="AI" align="absmiddle"> · reviewed by <img src="badges/human.svg" alt="human" align="absmiddle"> · approved by <img src="badges/human.svg" alt="human" align="absmiddle"> at `a1b2c3d`)</sub>

Each value is a small badge: blue for `human`, purple for `AI`. Two colours and nothing else, so the line stays balanced and quick to read. The short form below has no badges: with no person involved there is nothing to set apart. The words are always written this way: `human` in lower case, `AI` in upper case.

### Short form: all AI

When no person took part in any step, one short line replaces the full one:

```markdown
<sub>(**[AI transparency](README.md):** all **AI**, not reviewed by a human)</sub>
```

<sub>(**[AI transparency](README.md):** all **AI**, not reviewed by a human)</sub>

As soon as a person does any step, switch to the full line.

### The four steps

| Step | Values | Meaning |
|---|---|---|
| proposed by | `human` or `AI` | Whose idea the document was. `AI` when an agent wrote it on its own, for example a worklog |
| drafted by | `AI`, `human`, or both (`AI` `human`) | Who wrote the text. Both when one wrote and the other edited substantially; the main writer comes first |
| reviewed by | `human`, `AI`, both, or `—` | Who read it and commented. A review does not approve |
| approved by | `human` at a short commit hash, or `—` | A human read the whole document as it was at that commit and was happy with it. Only a human approves |

A step not done yet is a plain dash, `—`.

### Approval and the commit hash

The hash names the commit whose version of the document was approved; a commit cannot contain its own hash, so it is the commit before the one that writes the approval. The approval records that the whole document was approved once, at that version. Later edits do not change or remove it, and nothing checks for them: a reader who wants to know what changed since compares the document with that commit. A new approval replaces the hash.

### Fallback: plain text

Where images do not render (a terminal, a commit message, a plain-text export, another repository without the badge file), write `human` and `AI` in bold instead of the badges and leave out the smaller text and the link:

```markdown
(**AI transparency:** proposed by **human** · drafted by **AI** · reviewed by **human** · approved by **human** at `a1b2c3d`)
```

The badge version also falls back by itself: each badge has its word (`human` or `AI`) as alt text, so a viewer that does not load images shows the word.

### Badge files

`badges/human.svg` and `badges/ai.svg` in this repository; copy them into your repository (for example to `docs/img/transparency/`). Each is written as an HTML `<img>` with `align="absmiddle"` so that it sits in the middle of the line; a plain Markdown image sits on the baseline and looks raised. Adjust the relative path to where the file is.

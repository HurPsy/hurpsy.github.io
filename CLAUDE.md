# Working rules for hurpsy.github.io

These rules apply to every Claude session in this repository. The repository holds the source of the HurPsy project site, https://hurpsy.github.io, built with Material for MkDocs.

## What the site is for

- **Audience:** international researchers, grant reviewers, and anyone who wants to see what HurPsy does. The pages are in English.
- **No code on the pages:** the site shows what the apps do and how to use them, never HurPsy's source code. A later series on HurPsyLib's main classes is planned, but only when the user asks for it.
- **Other tools:** HurPsy doesn't compete with other experiment software. When the other tools come up, use the user's framing: HurPsyDesign was born out of necessity, to help junior researchers who were unfamiliar with, or not yet efficient in, the widely used tools such as PsychoPy, OpenSesame, E-Prime, Presentation, Inquisit and jsPsych. Make no comparisons.
- **Sources:** never invent citations. Cite a paper only after checking that it exists and says what the page claims; otherwise phrase the claim so that it needs no source.

## The HurPsy code repository

The apps live in a separate repository, `C:\Users\freeb\source\repos\HurPsy`. Read it to check facts (property names, menu items, how a test experiment is built), but never change anything there from this repository. Its own `CLAUDE.md` describes the projects.

### HurPsy's memory

Before writing or revising a tutorial page, read the HurPsy environment's memory index, `C:\Users\freeb\.claude\projects\C--Users-freeb-source-repos-HurPsy\memory\MEMORY.md`, and the notes on the page's feature, even when the user doesn't ask for it.
The memory is a map of the user's past decisions, and some notes are out of date or record ideas that were dropped.
What a page says comes from the HurPsy repository itself: its code, its checklist and settings files, its `Plans` folder and its commit messages.
When the page plan names a version, read the code at that version's tag.
Pages teach the general concepts, not the exact machinery behind every feature, and the version warning already says that the apps change, so don't fact-check every detail against the latest code.
When a memory note and the code disagree in a way that would change a concept the page explains, tell the user before writing it into a page.
Never change HurPsy's memory from this repository.

## Tutorial pages

- **The user's page plan comes first:** the user brings a page plan, usually a .docx in `C:\Users\freeb\Documents\HurPsyArchive` with notes and the user's own screenshots. Read it with `pandoc` and take the pictures out with `pandoc --extract-media`. Write the page from the plan, in the order of its notes.
- **A draft in chat comes before the page:** before writing the `.md` file, show the user the whole page as a draft in chat, in the order of the plan, with a placeholder such as *[picture: stimulus-set.png]* where each screenshot goes. Under the draft, list only the places where the code or HurPsy's memory would change a concept the plan explains. Write the page file, copy the pictures and update `mkdocs.yml` and `docs/index.md` only after the user has gone through the draft.
- **The user's corrections go into memory:** when the user corrects the draft, save in this environment's memory what was learned about a feature: where the reading of the code was wrong, how the user wants the feature explained, and what a page should leave out for now. Date each note and name the version it applies to. Don't save facts the code already records, such as property names or menu items.
- **Pictures are the user's screenshots.** There is no tutorial mode or picture script. Later tutorials will be shorter, with fewer pictures.
- **Style:** a friendly "we" voice, a paragraph or two per point, and the picture right after the text it illustrates. Every picture gets alt text that says what it shows. Use the app's own labels in bold (**Stimulus Sets**, **Use count within block**).
- **The version warning:** every tutorial page starts, right under its title, with the line `--8<-- "version-warning.md"`, which pulls in `includes/version-warning.md`. Change the wording only in that file.
- **File names:** a page is `docs/tutorial-N-short-name.md`, and its pictures go in `docs/images/tutorial-N/`, named after what they show (`stimulus-set.png`, not `image7.png`).
- **Navigation:** every new page gets a line under `nav:` in `mkdocs.yml`. Tutorial pages go under `Tutorials`, as `"N. Title": tutorial-N-short-name.md`. When a tutorial is added, also update the Tutorials section of `docs/index.md`.
- **Status page:** `docs/status.md` says what works today and what comes next. Update it only when the user asks.

## Checking a change

- Build with `.venv\Scripts\mkdocs build --strict` before reporting a change. The publishing workflow builds in strict mode too, so a warning here would stop the site from publishing.
- For a look in the browser, the `site-preview` configuration in `.claude/launch.json` runs `mkdocs serve` on http://127.0.0.1:8000.
- Material for MkDocs reaches end of life on May 5, 2027; Zensical is its successor. Don't migrate unless the user asks.

## Branches, commits and publishing

- **Branch names:** `MM-dd-NN-short-kebab-description`: the month and day, then a two-digit running number for that day, then a short description, as in `11-22-01-tutorial-1-introduction`. For NN, take the highest number among the existing branches with today's prefix and add 1, or start at 01.
- **A branch per task:** every new task that changes files starts on a new branch, made off whatever branch is checked out. Corrections to the task in progress stay on its branch.
- **Commit messages:** they start with "ClaudeCode" and say in one sentence what was done, as in "ClaudeCode added the first tutorial page: ...".
- **Asking first:** commit only when the user asks, and never push or merge without being asked. A push to `master` publishes the site within a minute or two, through `.github/workflows/publish.yml`.
- **"send it over"** means, in this repository: commit any uncommitted work on its branch, fast-forward `master` to it, and push `master`. There are no version tags and no documentation rebuild here; those belong to the HurPsy repository. Stop and ask if the merge is not a fast-forward.
- **"bring it down"** means: fetch origin, fast-forward `master`, list any new branches without merging them, and report.

## Writing style

- Write plain sentences that non-coders can read, with a subject in every sentence. Avoid sentence fragments and brief labels on the pages: almost always write a complete sentence instead. Comments in configuration files are full sentences too: "This workflow builds the site...".
- Bold a project name (HurPsyDesign, HurPsySession, HurPsyRun, HurPsyLib) only the first time a page introduces it, and write it plain after that. Bold is otherwise kept for the app's own labels, such as **Stimulus Sets**, and for terms being defined. When the user's own text bolds a project name past its first mention, or leaves the first mention plain, point it out and correct it.
- Act only when the user's message has a clear action verb such as "add", "change", "write" or "send". Without one, discuss: observations, options, a recommendation, questions.

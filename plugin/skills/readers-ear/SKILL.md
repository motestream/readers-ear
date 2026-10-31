---
name: readers-ear
description: Writes and revises prose in any language and genre so that it reads naturally to its intended reader. Use when writing text that people other than the user will read, such as emails, articles, documents, posts, slides, speeches, fiction, translations, UI text, commit messages, and PR descriptions, and when reporting to the user, in the final answer after working on the user's request or in a document made for the user to read, even when the user hasn't asked for help with the wording. Also use when the user asks to revise or polish text, or to make it sound natural or less AI-like, and for all prose the agent writes when the user's saved instructions say so.
---

# Reader's Ear

Make the text you write or revise read as if a skilled writer of its language and genre had written it for its intended reader.

## The standard

Measure the text against its intended reader, not against rules. Ask what this reader already knows, what they need from the text, how they relate to the writer, and what they expect from its genre and language. Whether a word, a sentence, or an organization works depends on those answers, so the same choice can be right in one text and wrong in another. Keep the set phrases the genre calls for, even where they look formulaic.

To find what this reader already knows, separate what they have seen from what only you know. When the reader is the user, what they have seen in the conversation is their own messages, your final answers to their requests, and the documents you made for them. Treat everything else as unseen, including what you wrote in the conversation while working toward an answer, your reasoning, tool output, reports from subagents, and the names you gave things while working. Beyond the conversation, the user knows what they bring from their own work and field.

Judge the text by the norms of its own language, not by those of English (the language of these instructions) or of the language you think in.

Writing samples and style guides the user provides take precedence over this skill. If the user hasn't said who the reader is, infer it from the text and the request.

## Writing new text

Use this when you write text yourself from information you have, including when you translate.

Before drafting, answer the questions in "The standard" for this reader. Decide what this reader is reading the text for, such as making a decision, running a command, learning where things stand, or enjoying a story, and from that purpose, what they need to come away with and what they need first. Choose the organization that the genre and this reader expect; for a translation, keep the source's organization (the order of its sections and points) unless the user asks you to adapt it. Then write the draft for that reader, following the norms of the text's language and genre.

After drafting, read the draft once as its reader would, and fix the concrete problems you find by the criteria and methods in "Revising text". If the draft already reads well, leave it as it is.

## Revising text

Use this procedure to revise existing text.

Read the text as its intended reader would, meeting it for the first time. A problem counts only if you can point to it:

- a place where this reader would stumble, lose the thread, or not find what they need when they need it
- a place where a skilled writer of that language and genre wouldn't have written that way, and you can say how they would have written it
- a passage that gives this reader nothing they need

To judge the last, ask whether the text would serve this reader's purpose any less well without the passage.

Problems occur at every scale: a word, a sentence, a passage, or the organization of the whole text. Look at every scale.

Fix each problem at its own scale. Cut a passage that gives this reader nothing they need; in text the user supplies, do this only on a general request (see "Text the user supplies"), and say what you cut. In a translation, keep everything the source says, and keep its organization unless the user asks you to adapt it. Fix a problem in the organization by rebuilding, not rewording: list what the text has to convey, rebuild the affected part in the order the reader needs, and compare the rebuilt part with the original for anything lost, changed, or added.

Change the text only to fix concrete problems, and keep a fix only if the text is better with it. Stop when no concrete problem remains, so that good text comes out almost unchanged. Match the time you spend to the text's length and stakes.

## Two problems to check for

When you read a draft or a text as its reader, check specifically for these two problems.

**Interference from other languages.** Languages other than the text's own leave traces, even languages that appear nowhere in the input or in your reasoning. Look for the signs rather than trying to name the source language: word order, phrasing, collocations, idioms, punctuation and quotation marks, number and date formats, or forms of address carried over from another language. Look also for foreign words this reader wouldn't use, and for mixed regional spellings, scripts, or vocabulary.

**Context the reader hasn't seen.** Look for places that rely on something the reader hasn't seen (see "The standard"), such as your conversation with the user, notes the reader doesn't have, or names you gave things while working. For each name, term, and reference to something earlier, ask where this reader would have learned it. If you can't point to the place, say it in words this reader knows, such as the ones they used themselves, or, if they need the term, explain it where it first appears.

## Text the user supplies

When you revise or translate text the user supplies:

- Keep the author's facts, points, and voice, and change no more than the request calls for.
- Treat a general request (revise, polish, make it sound natural or less AI-like) as covering every scale. A narrow request, such as fixing typos, doesn't cover larger problems: point out, instead of fixing, the ones that would mislead or confuse the reader, such as factual errors, and make no suggestions about style.
- Point out, rather than fix, factual errors and any ambiguity that only a guess at the author's meaning could resolve. An inconsistency you can resolve from the text's own facts, such as an instruction that conflicts with a time the text gives, is a problem to fix, not to flag.

## In every task

- Use only the facts, figures, and quotations you have. The one exception: when text the user supplies offers only generalities and the request covers making it read naturally or less AI-like, you may add widely known, accurate general information, such as how a common technique works. Never add experiences, data, quotations, or claims about the user or their organization, and list everything you added.
- If information is missing, ask the user, and write the sentence that needs it with a bracketed placeholder, so that the text is ready once the user fills it in. When you can't ask, such as when running unattended, mark the gap in the text the same way.
- If you're unsure of your judgment in the language or the subject, change less and say so.
- Deliver the finished text plus what the user needs to know, including the points you flagged instead of fixing and, if you reorganized the user's text, a sentence on why. Leave out working notes and drafts unless the user asks for them.

## Careful mode

Use careful mode only when the user explicitly asks for a slower, more thorough job, in the conversation or in their saved instructions, because it costs far more time and tokens. In careful mode, you get outside views of the text from two fresh contexts before you judge it yourself. Fresh contexts are ones that haven't seen the conversation, such as new subagents, not copies or forks of the current one. Give each only what's listed below, and none of your own observations or suspicions about the text.

- **Reference reader.** Give it the text's language, intended reader, and genre, a rough idea of its purpose, and the source rules below, but not the text. Ask it to find a few texts of the same genre and purpose that meet the rules, and to read them in full rather than relying on search snippets. It reports which sources it used and how those texts are written: structure, set phrases, length, register, and anything else the genre expects.
- **Cold reader.** Give it only the text and a note on its reader and purpose; for a translation, give it the translation, not the source. Ask it to read as that reader would. It reports where it stumbles or loses the thread, and what it takes the main point to be.

Then work through these steps:

1. **Get both reports.** When revising, start both readers at once. When writing new text, including a translation, run the reference reader first and draft with its report in hand. Then give the finished draft straight to the cold reader, without the read-through in "Writing new text"; you read it yourself in step 2. If fresh contexts aren't available, skip the cold read and find and read the references yourself: before you look for problems when revising, or before you draft when writing new text.
2. **Read the text yourself.** With the reports in hand, read the text and list its problems. Treat the reports as evidence to weigh against your own reading, not as a list of changes to make.
3. **Check against sources.** Check the terms, names, figures, and spellings the text depends on, and any point you're unsure of, against current authoritative sources such as dictionaries, usage guides, and official sites. Because the user's text may be confidential, search with terms, names, and short phrases, not passages of it.
4. **Revise.** Work as in "Revising text". Use the references as a standard to measure the text against, not as wording to copy. In the user's text, the author's facts, points, and voice take priority over the references.
5. **Report.** Tell the user briefly what you consulted and what it changed, and name every step you skipped or couldn't do.

**Source rules** (for steps 1 and 3). Use sources originally written in the text's language, whose wording a person or organization has checked and takes responsibility for. Translations, including the translated pages of multilingual sites, don't qualify, because they can carry the patterns of their source language. The one exception is in step 3: to check how an organization writes its own names and terms, you may use its official pages in the text's language. For phrasing and genre conventions, use text of the same genre and purpose, such as:

- pages of public institutions, large companies, major news organizations, and established publishers
- work by respected writers in the genre
- text from curated corpora

Don't use text whose wording no one appears to have checked, such as anonymous pages, sites that mass-produce articles, and automatically generated summaries.

## Scope

The scope matters only when no one has asked you to use this skill: it decides which text you apply the skill to on your own. Whatever the scope, always revise what the user asks you to revise. There are three scopes:

- **Text for others and reports to the user** (the default): text for others, as defined below, and your reports to the user. A report is either your final answer to a request the user makes to you directly, when you did work to answer it, such as reading files, running commands, or delegating to subagents, or a document or other material you make for the user to read. What you write in the conversation while working toward the final answer isn't a report, and neither is a short reply you can give from the conversation alone.
- **Text for others**: text you write whose final readers are people other than the user.
- **All prose**: all prose you write.

If no scope is set in your instructions or memory, use the default. After you deliver the first text in the default scope, ask the user whether they want to keep this scope, apply the skill to all prose you write, or apply it only to text for others, if all of these hold:

- You're working with the user interactively, not as a subagent or unattended.
- The user can make this choice. An end user of someone else's product, for example, can't.
- There is a suitable place to save the answer.

Ask this only once across all sessions. If the user moves on without answering, treat that as a choice of the default and save it as described below, so that no later session asks again.

When the user answers, or later changes the scope, save the choice as one sentence in the user's language that names the skill and the scope. In English, for example: "Use the readers-ear skill on text you write for other people to read and on your final answers and documents for me.", "Use the readers-ear skill on all prose you write.", or "Use the readers-ear skill only on text you write for other people to read."

Save the sentence somewhere personal that every future session loads, such as a user-level instruction file or account memory, rather than a file shared with a team, memory limited to one project, or a place that won't be loaded next time, such as a disposable cloud environment. Tell the user where you saved it. If the user changes the scope where no such place exists, apply the choice to the current conversation only, say so, and give the user the sentence to paste into their own instructions.

When you apply the skill without being asked, work only on the text you write yourself, and leave text by other people as it is, even in the same file. If you're applying it inside another task, such as writing a commit message or a report to the user, deliver the text as that task requires and mention only what the user needs to know.

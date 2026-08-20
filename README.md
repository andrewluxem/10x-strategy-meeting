# 10x-strategy-meeting

A small, static agent skill that runs a strategy session reaching for an order of magnitude. Ask it for one thing and it hands back a working document, not a lecture about moonshots.

Two artifacts:

- **Session Packet**: what you send to the room. The 10x question in one sentence, attendees split into groups of three with Idea Generator, Challenger, and Note Taker roles, a framing block that names the assumption the team is allowed to drop, blocks scaled to the slot you actually have, and the seven starter questions rewritten in your product and market terms.
- **Session Capture**: what survives the room. One entry per idea with its what, its why, the discussion, a scale check, and a data check, ten percent ideas kept and labeled incremental rather than dropped or dressed up, and a routing table where every idea carries a next step, an owner, and a date.

It executes the [10x Strategy Meeting playbook](https://www.andrewluxem.com/playbooks/10x-strategy-meeting) from andrewluxem.com. The playbook page teaches the framework. This skill runs it.

**Static by construction: no network calls, no remote fetch, no auto-update, nothing scheduled, no background behavior. Model-invocable by design: an agent may pick it up when you ask for 10x session work, and naming the skill is the reliable path.** It reads nothing outside its own folder, never edits your global agent config, and never updates itself in place. The whole thing is one `SKILL.md` you can read in five minutes, plus two templates and one reference file it loads only when a step needs them.

## The loop

Pick the mode from what you bring. Context and a future session mean Prep. Notes from a session that already happened mean Capture. If both, prep is stale, so it runs Capture.

| Mode | You bring | You get |
|---|---|---|
| **A. Prep** | Business context, attendee count, time slot | Session Packet |
| **B. Capture** | Raw session notes from one or more groups | Session Capture |

The format rests on one rule, and the whole session is built to protect it:

**Why, not how.** The session asks why we should get there, never how we would build it. How-thinking collapses the idea space to what the team already knows how to build, which is exactly the ten percent path the session exists to escape. Feasibility objections are out of order during generation and get redirected to the challenge block.

That rule is why the roles exist. The Idea Generator proposes and does not self-censor. The Challenger asks what would have to be true, never that will not work, and stays quiet until the challenge block. The Note Taker documents the why alongside the what, because the why is what survives into goals.

What it refuses to shortcut:

- **Feasibility stays out of generation.** A packet that gates ideas on how-thinking has broken the mechanism the format exists to protect.
- **Never pad an incremental idea into a moonshot.** Label it incremental and keep it. Dressing ten percent as 10x is the failure the session exists to expose.
- **Nothing in a captured entry is inferred.** Every sentence traces to something the notes record. A hedge like inferred or likely does not license unrecorded content; the only substitute for missing content is the gap label, Not recorded or None noted.
- **An assumption that is not visible is an invention.** Where an input is absent, the assumption appears in the artifact where the value sits.

A full strategic plan is not this skill's artifact. When you ask it to turn session output into goals or a roadmap, it produces the Session Capture and names the destination by slug: `business-goals` for measurable goals, `how-to-plan-new-product-and-services` for a phased plan.

See [`examples/example-run.md`](examples/example-run.md) for a full Mode A pass, from a twelve-person team with two hours to a packet the owner can send.

## Install

**Manual (recommended, clone and copy):**

```bash
git clone https://github.com/andrewluxem/10x-strategy-meeting.git
cp -r 10x-strategy-meeting/skills/10x-strategy-meeting ~/.claude/skills/
```

Then invoke it: `use the 10x-strategy-meeting skill to prep a 10x session for my team`.

**As a Claude Code plugin (version-pinned, no auto-update):**

```
/plugin marketplace add andrewluxem/10x-strategy-meeting
/plugin install 10x-strategy-meeting@10x-strategy-meeting
```

`plugin.json` carries an explicit `version`. Installing pins that version. It does not silently pull new commits. Taking an update means bumping the version and reinstalling, so the update is a decision rather than a background event.

**As a zip:** the packaged skill is on the playbook page at [andrewluxem.com/playbooks/10x-strategy-meeting](https://www.andrewluxem.com/playbooks/10x-strategy-meeting), for platforms that want a folder upload instead of a clone. Same files, apart from a `metadata:` block in the site copy's frontmatter that the site registry and packager read.

Portable by design: it is plain Markdown with no runtime, so it works anywhere a folder of skill files works.

## Usage

```
Set up a 10x strategy session for my ecommerce team, 12 people, two hours
Here are the whiteboard notes from our 10x session, turn them into something we can act on
We keep planning 10 percent improvements, help us think 10x about the newsletter business
```

Naming the skill is the reliable path: `use the 10x-strategy-meeting skill`. It has no background behavior and nothing scheduled, so nothing happens until a request goes to it.

## Iterating

The skill is the folder [`skills/10x-strategy-meeting/`](skills/10x-strategy-meeting/):

- `SKILL.md` is the procedure, and it is the only file loaded every time.
- `references/facilitation-notes.md` is the depth: role boundaries, why-not-how, assumption removal, and the four failure modes. It is read at the step that needs it.
- `assets/` holds the two templates the artifacts are built from. Each carries a filled example under the blank one, and the capture example deliberately includes an idea that arrived as a bare what, so its why reads Not recorded rather than a reconstruction.
- `meta.yaml` carries the version, the invocation examples, the three test prompts with their pass bars, and the changelog.

Edit it, invoke it on a session you are actually running, and see whether the artifact earns its place. The bar is that the output would have taken you an afternoon to build by hand.

When you change behavior meaningfully, bump `version` in both `.claude-plugin/plugin.json` and `meta.yaml` so plugin installs pick it up deliberately, and add the changelog line.

## Testing

`meta.yaml` ships the three prompts this skill is scored against, each with its own `passes_when` bar: a happy path, a messy input, and a near miss it should hand off rather than answer. The bars live with the skill on purpose. A prompt that exists only in a chat transcript is gone by the next run, and a bar rewritten after seeing the output grades itself easier every round.

Version 1.0.0 was tested on Claude Code. It has not been exercised on other hosts.

## License

MIT, see [`LICENSE`](LICENSE). The skill folder carries the same MIT text in [`skills/10x-strategy-meeting/LICENSE.md`](skills/10x-strategy-meeting/LICENSE.md), so the whole repo is one license.

---

## More playbooks

This skill packages one playbook from the free library at [github.com/andrewluxem/playbooks](https://github.com/andrewluxem/playbooks). Every playbook is free to read, with no email required.

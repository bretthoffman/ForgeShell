# ╔══════════════════════════════╗
# ║        F O R G E S H E L L   ║
# ║   reusable autonomous shell  ║
# ╚══════════════════════════════╝

## Greetings!

Welcome to ForgeShell.

ForgeShell is a reusable autonomous shell that takes a PRD and turns it into a real project workflow:

- PRD intake
- planning docs
- execution packages
- implementation
- testing and validation
- git-backed package closeout
- hardening
- functional fidelity uplift
- high-end design refinement
- final closeout
- optional handoff cleanup

It is the project engine, not the final product.

---

## What ForgeShell actually does

ForgeShell reads your PRD, plans the work, executes it in controlled packages, validates completed units, commits progress, continues through hardening, runs a functionality uplift pass against the PRD, runs a design polish pass, and leaves you with a structured project build plus the history of how it got there.

Think of it as a guided project builder with rules, checkpoints, and cleanup behavior.

---

## Folder layout

This folder contains:

- `shell-core/` → the actual ForgeShell engine
- `USER_INSTRUCTIONS.md` → this file

**Important:** Claude CLI or Codex CLI should operate inside **`shell-core`**, not the parent folder.

---

## Starting a new run

If you used the ForgeShell bootstrap flow, most setup is already handled for you:

- the repo has already been downloaded into a clean workspace
- your PRD has already been copied into `shell-core/raw_prd/`
- your application name has already been captured for possible final packaging
- your agent should already be opened inside `shell-core`

At that point, just type:

`begin`

or

`start`

That tells ForgeShell to inspect the current state and begin the correct workflow phase.

---

## How to resume

If the run stops, gets interrupted, or the session closes, type:

`continue`

ForgeShell is designed to inspect the current repo state, logs, artifacts, and git state, then resume from the nearest unresolved point.

You should not normally need to tell it package numbers manually.

---

## If you are not using bootstrap

If you started ForgeShell manually instead of with the bootstrap launcher:

1. open your agent inside `shell-core`
2. place exactly one PRD `.md` file in `shell-core/raw_prd/`
3. make sure the workspace is ready
4. type `begin`

Rules for `raw_prd/`:
- exactly one top-level regular `.md` file
- no extra PRD files
- no PRD subfolders
- remove junk files like `.DS_Store` if they appear there

---

## External services and env vars

ForgeShell does not invent third-party credentials for you.

But in most cases, ForgeShell can still build the application structure **before** those services are fully configured.

That means if your PRD mentions tools like:

- Clerk
- Convex
- Supabase
- Stripe
- analytics providers
- storage providers
- external APIs

ForgeShell will usually try to:

- scaffold the app around those integrations
- use placeholders and environment-variable expectations where appropriate
- continue building as long as the integration is not a true build blocker

### What this means in practice

You do **not** usually need to fully configure every external service before starting.

Instead, ForgeShell will often:

- build the app structure first
- leave provider setup to you afterward
- tell you at final closeout what still needs to be configured

Examples of remaining setup after the build may include:

- creating a Clerk app
- adding Clerk keys
- creating a Convex project
- running `npx convex dev`
- adding required environment variables
- connecting hosting or deployment services
- verifying the final auth/backend flow locally

### When ForgeShell may still stop early

If an external integration is a **true build blocker**, ForgeShell may escalate before continuing.

That should only happen when:
- the PRD clearly requires the integration
- the integration is necessary for meaningful generation or execution
- ForgeShell cannot safely scaffold around it with placeholders, structure, and setup notes

---

## What to expect during a run

ForgeShell will usually move through these phases:

### Phase A — Intake
It reads your PRD and creates:

- `PRD_SOURCE.md`

### Phase B — Planning
It creates planning artifacts like:

- `CURRENT_STATE_AUDIT.md`
- `MASTER_ROADMAP.md`
- `EXECUTION_PACKAGES.md`

### Phase C — Execution
It executes packages in order.

If the next package is too vague, it narrows and expands that package before continuing.

### Phase D — Hardening
After the main implementation is functional, ForgeShell continues through hardening and validation work, including the final audit and hardening outputs that support a stable next pass.

### Phase E — Functional Fidelity Uplift
After the minimally working build is in place, ForgeShell runs a structured pass against:

- the original raw PRD
- `PRD_SOURCE.md`
- the built application

This phase is meant to catch:
- drift
- omissions
- compressed intent
- thin or partial implementation
- meaningful gaps between the original vision and the built product

ForgeShell should then uplift the application in a controlled way and explicitly record what still remains deferred.

Typical artifacts from this phase include:

- `POST_BUILD_FIDELITY_AUDIT.md`
- `FIDELITY_UPLIFT_PLAN.md`

### Phase F — High-End Design Pass
After the functionality uplift, ForgeShell runs a dedicated visual and UX refinement pass.

This phase is meant to improve things like:

- visual hierarchy
- spacing
- layout
- typography
- surfaces and cards
- color system
- responsiveness
- navigation clarity
- polish and personality

It is not supposed to remove useful functionality. It is supposed to make the product feel more intentional, cohesive, and production-quality while preserving the app’s mechanics.

Typical artifacts from this phase include:

- `DESIGN_DIRECTION_BRIEF.md`
- `UI_REFINEMENT_PLAN.md`
- `POST_DESIGN_FUNCTIONAL_VALIDATION.md`

### Phase G — Post-Uplift Validation
ForgeShell keeps a validation checkpoint after the fidelity and design passes so the application can be checked again before final closeout.

### Phase H — Final Closeout
After the product has been implemented, hardened, uplifted, and refined, ForgeShell completes final closeout.

### Final closeout expectations
If your PRD requested external integrations that were scaffolded but not fully configured live, ForgeShell should include a final section telling you what still remains to be done.

That may include things like:
- provider setup
- API keys
- env vars
- backend creation
- CLI sync commands
- deployment connection
- final verification steps

### Phase I — Optional final packaging
After a fully successful run, ForgeShell may offer two choices:

1. **Clean for handoff**  
   Archive ForgeShell runtime logs and final shell artifacts, remove shell internals from the final app repo, rewrite the README for your application, trim shell-specific `.gitignore` entries, and rename `shell-core` to your application name.

2. **Leave workspace as-is**  
   Keep the finished application inside the full ForgeShell workspace with all shell files intact.

---

## Git behavior

ForgeShell uses git as part of its workflow.

On a fresh run, if `.git` does not exist yet, it may:

- initialize local git
- verify git works
- continue from there

As work progresses, ForgeShell is designed to:

- commit completed units of work
- keep package boundaries clean
- inspect status and diff information during closeout
- avoid carrying messy incomplete changes across completed units

### Important
ForgeShell does **not** automatically:
- create a GitHub repo for you
- add a remote
- push your work to GitHub

That remains your job after review.

---

## What you should end up with

By the end of a successful run, you should have:

- a normalized PRD
- planning docs
- execution packages
- implemented project work
- validation and test evidence
- git history with completed units
- hardening outputs
- functional fidelity audit and uplift outputs
- design refinement outputs
- final closeout output
- optionally, a cleaned handoff-ready application folder

In other words:

**you start with a PRD, and you end with a structured project build plus the records showing how it was created and refined.**

---

## If ForgeShell escalates

Sometimes ForgeShell may stop and raise a structured escalation.

That usually means it hit a real blocker and needs:
- a decision
- missing input
- clarification
- or confirmation before it can continue safely

If that happens:
1. read the escalation carefully
2. provide the requested input
3. type `continue`

---

## Best operator habits

- run Claude or Codex inside `shell-core`
- use bootstrap when possible
- keep PRD input clean and singular
- use `begin` to start
- use `continue` to resume
- let ForgeShell finish units cleanly before interrupting
- review final outputs before publishing or deploying

---

## Final steps after ForgeShell is done

Once ForgeShell finishes and you are happy with the result:

1. review the generated project and docs
2. verify the final app and build state
3. read any remaining external setup steps in the final closeout output
4. choose whether to clean for handoff or leave the workspace as-is
5. connect the project to your remote git provider if needed
6. push the repo or branch
7. connect hosting or deployment services
8. finish any live third-party setup still needed
9. do your normal final human review before release

ForgeShell gets you very far, but you still own the final launch.

---

## Very short version

If you just want the short version:

1. get into `shell-core`
2. make sure your PRD is in place or use bootstrap
3. type `begin`
4. if interrupted, type `continue`
5. let ForgeShell scaffold external integrations when possible
6. let it run through functionality uplift and design refinement
7. when done, review the remaining setup steps, package if desired, and push or deploy

---

## Thank you

Thanks for using ForgeShell.

Build cool stuff, enjoy the process, and have fun.
# LabDesk: design package (DBIZ2 worked example)

> Worked example for teaching, DBIZ2 Digital Business Project II (VJCBI College, Foreign Trade
> University). Not a real product and not a student submission.

**LabDesk** is a seat reservation system for the faculty computer labs. Students book a seat before
they come and check in with a QR code at the lab door; seats nobody uses are released after 15
minutes; Lab Technicians block faulty seats and watch how labs are used.

This repository holds the **design package only**: requirements, analysis and external design,
written in DBIZ2. There is no code yet. In DBIZ3 a team and its AI coding agent build LabDesk
from these files.

**This README is written for two readers.** People start at section 8 (reading order). AI agents
read sections 1 to 7 before any task and follow them.

---

## 1. Rules for AI agents

1. **The files are the source of truth, not your general knowledge.** If a fact is not in this
   repository, it is not decided. Do not fill the gap with a typical solution.
2. **Every fact has one owning file** (section 3). Read the owner before you use a fact. To change
   a fact, change it in the owner first, then update the files that cite it.
3. **Refer by ID, never retell.** Write `FR-01-03`, `BR-02`, `S-F01-02`; do not copy the
   sentence. A retold sentence drifts from its source.
4. **Do not invent IDs.** A new item takes the next free number in its owning file (section 4).
   Never reuse or renumber an existing ID, even when the item is removed; mark it removed instead.
5. **Stay inside scope.** Build or design only what W1 lists. Everything in W0 Table 3
   (Won't-have) stays out, even if it seems useful. The priority that counts is the **effective
   priority** in W4, not the initial priority in W1.
6. **When something is missing or unclear, ask; do not guess.** Add a row to the Open questions
   table of the file you are working on, written as `[NEEDS CLARIFICATION: <question>]`, and mark
   whether it blocks the work. A guess written as a decision is the most expensive kind of error.
7. **Screens follow the external design exactly.** Elements, states and navigation come from the
   Screen Spec; colours, fonts, spacing, corners and frame width come only from the design tokens
   in `ui-conventions.md`, section 6. The Element names in section 3 of a Screen Spec are the
   component names; the numbers on `*-numbered.png` match its `#` column.
8. **Do not edit history.** Accepted ADRs are not rewritten: a new ADR supersedes an old one.
   Change log rows, verification log rows and `ai-log.md` rows are only appended.
9. **Do not edit images by hand.** Images in `screens/img/` are exports from the team's drawing
   tool. If a screen changes, say which image must be redrawn.
10. **Report what you changed and what you could not check**, file by file, at the end of the task.

## 2. Repository map

Each lesson writes into its own folder.

```text
README.md                    this file
docs/
  project/                   Lessons 1-2   project-brief.md, ai-log.md
  context/                   Lesson 3      cvca.md, context-diagram.md
  use-case/                  Lesson 4      use-case-diagram.md, SD-<UC-ID>.md
  architecture/              Lesson 4      architecture.md, adr/ADR-<nnn>-<title>.md
  function-list/             Lessons 5-6   w0-scope.md, w1-function-list.md, w2-cost.md,
                                           w4-priorities.md, w5-handover.md, w6-cash-flow.md
  activity/                  Lesson 7      activity-index.md, AD-<UC-ID>.md
  external-design/           Lesson 8      usage-flow.md, screen-list.md, screen-transition.md,
                                           ui-conventions.md
    screens/                 Lesson 8      screen-spec-<Screen ID>.md
      img/                   Lesson 8      <Screen ID>.png, <Screen ID>-numbered.png,
                                           <Screen ID>-<state>.png
```

## 3. Which file owns which fact

| Fact | Owning file | Cited by |
|---|---|---|
| Product name, client, team, roles, milestones | `docs/project/project-brief.md` | every file |
| Stakeholders, value flows, stakeholder requirements `StR-xx` | `docs/context/cvca.md`, section 3 | architecture |
| System boundary and external entities | `docs/context/context-diagram.md` | use case diagram, AD lanes |
| Actors and use cases (diagram) | `docs/use-case/use-case-diagram.md` | W0, AD, usage flow |
| How the system's parts talk for one use case | `docs/use-case/SD-UC-xx.md` | W1 source trace, AD |
| System requirements `SyR-xx`, functional and physical design | `docs/architecture/architecture.md` | ADRs, W1 |
| Technical decisions `ADR-nnn` | `docs/architecture/adr/` | W1, architecture |
| Use case inventory `UC-xx` and its feature | `docs/function-list/w0-scope.md`, Table 1 | AD index, usage flow, screens |
| Features `F-xx` | W0 Table 2 | W1, screen IDs |
| Won't-have (out of scope) | W0 Table 3 | everyone: never build these |
| Data groups (what is stored) | W0 Table 4 | Screen Spec data sources |
| Business rules `BR-xx` | W0, "Business rules" | W1, AD, Screen Spec |
| Functions `FR-xx-yy` with the EARS acceptance criterion | `docs/function-list/w1-function-list.md` | AD, Screen Spec, tests |
| Effective priority (Must, Should, Could) | `docs/function-list/w4-priorities.md` | screen list, build order |
| Cost, scenarios, baseline for DBIZ3 | `w2-cost.md`, `w5-handover.md`, `w6-cash-flow.md` | project decisions |
| Behaviour of one use case, its branches, object states | `docs/activity/AD-UC-xx.md` | Screen Spec states, tests |
| Which use cases have a diagram, and why not | `docs/activity/activity-index.md` | |
| Order in which an actor uses the use cases | `docs/external-design/usage-flow.md` | screen transitions |
| Screens `S-Fxx-nn` | `docs/external-design/screen-list.md` | everything about screens |
| Navigation between screens | `docs/external-design/screen-transition.md` | Screen Spec section 5 |
| Language, formats, components, messages, design tokens | `docs/external-design/ui-conventions.md` | every screen |
| One screen: elements, states, interactions, rules `SR-nnn` | `docs/external-design/screens/screen-spec-S-Fxx-nn.md` | build and test |
| Mistakes AI made and what the team decided | `docs/project/ai-log.md` | |

## 4. IDs

| ID | Pattern | Example | Defined in |
|---|---|---|---|
| Stakeholder requirement | `StR-nn` | StR-01 | CVCA section 3 |
| System requirement | `SyR-nn` | SyR-01 | architecture.md section 1 |
| Decision | `ADR-nnn` | ADR-004 | `docs/architecture/adr/` |
| Use case | `UC-nn` | UC-01 | W0 Table 1 |
| Feature | `F-nn` (`F-00` = platform and access) | F-01 | W0 Table 2 |
| Business rule | `BR-nn` | BR-02 | W0 Business rules |
| Function (L2) | `FR-<feature>-<nn>` | FR-01-04 | W1 |
| Sequence diagram | `SD-<UC-ID>` | SD-UC-01 | `docs/use-case/` |
| Activity diagram | `AD-<UC-ID>` | AD-UC-05 | `docs/activity/` |
| Screen | `S-F<feature>-<nn>` (`S-F00-nn` = shared) | S-F01-02 | screen list |
| Screen rule | `SR-nnn`, local to one Screen Spec | SR-001 | Screen Spec section 6 |

The chain that every change must keep intact:

```text
StR -> SyR -> UC -> F -> FR (EARS) -> AD (cites FR on each system action) -> S (cites UC and FR)
```

## 5. How to do common tasks

**Before any task:** read this README, `project-brief.md`, then the owning files of the facts the
task touches (section 3).

**Change or add a function.** Edit W1 (ID, EARS criterion, source trace), then W4 (effective
priority and justification), then W2 and W5 if the cost changes. Then update every AD and Screen
Spec that cites the FR.

**Add a use case.** Add it to the Use Case Diagram, then W0 Table 1 with its feature, then its
functions in W1, then a row in `activity-index.md`, then its place in `usage-flow.md`.

**Add or change a screen.** Add the row to `screen-list.md`, the node and arrows to
`screen-transition.md`, the screen to the matching usage-flow step, and the Screen ID to section 5
"Screens touched" of each AD it serves. Then write the Screen Spec from
`screen-spec-S-F01-02.md` as the model, and list the images the team must draw.

**Build a screen (DBIZ3).** Read in this order: the Screen Spec, the FRs in its section 7, the BRs
its rules cite, the AD whose actions it covers, `ui-conventions.md`. Build every state in section
4. The acceptance tests are the EARS criteria of the FRs and the branches in section 3 of the AD.

**Check traceability.** Report five lists, with file and ID, and write "none" when a list is
empty. Do not change files while checking.

- A. FRs with a user-visible effect that no Screen Spec lists in section 7.
- B. Screens or elements that serve no FR.
- C. Actor actions in an AD with no Screen ID in its section 5.
- D. "Goes to" targets in a Screen Spec that are not in the transition diagram.
- E. Usage-flow steps with no screen, screens in no usage-flow step, usage-flow arrows with no path
  in the transition diagram.

## 6. Notation

- Diagrams are Mermaid code blocks inside the `.md` files. The activity diagrams use
  `swimlane-beta`, which needs Mermaid 11.16 or later; if a block does not render, paste it into
  [mermaid.live](https://mermaid.live). In flowcharts every label is in double quotes and no node
  is named `end`.
- Mermaid has no use case diagram type, so the Use Case Diagram is drawn as a flowchart.
- Interface text is in English; Vietnamese is available in settings (`ui-conventions.md`).
- Dates `dd/MM/yyyy`, times `HH:mm` (24-hour), money in VND with dots for thousands
  (`3.160.000`).
- Person-hours, rates and thresholds follow the class Parameters of the Lesson 5 workbook. The
  benefit figures in W6 are team estimates for teaching.

## 7. State of this example

The package is complete in structure and deliberately incomplete in a few places, so it can be
used for practice. An agent must not treat the gaps below as decided.

- Row 4 of the Lesson 7 Inputs check is still open, so `SD-UC-02` is not drawn yet.
- Only `AD-UC-01` and `AD-UC-05` are written out. The other diagrams named in
  `activity-index.md` (`AD-UC-02`, `AD-UC-04`, `AD-UC-06`) are Draft and have no file.
- Only one Screen Spec is written out: `S-F01-02` Seat map, with all five states and the numbered
  images. The other screens in `screen-list.md` have no Screen Spec yet.
- Open questions marked `[NEEDS CLARIFICATION: ...]` are listed in the AD and Screen Spec files;
  those with an answer show it in the last column.

## 8. Reading order for people

| Step | Lesson | File | What it shows |
|---|---|---|---|
| 1 | L1-L2 | [project-brief.md](docs/project/project-brief.md) | Client, problem, goal, team roles, milestones |
| 2 | L3 | [cvca.md](docs/context/cvca.md) | Stakeholders, money and information flows, problems, stakeholder requirements |
| 3 | L3 | [context-diagram.md](docs/context/context-diagram.md) | LabDesk as a black box and the entities around it |
| 4 | L4 | [use-case-diagram.md](docs/use-case/use-case-diagram.md) | Who wants LabDesk to do what; list of sequence diagrams |
| 5 | L4 | [SD-UC-01.md](docs/use-case/SD-UC-01.md), [SD-UC-04.md](docs/use-case/SD-UC-04.md) | How the parts of LabDesk talk for one use case |
| 6 | L4 | [architecture.md](docs/architecture/architecture.md) and [adr/](docs/architecture/adr/) | System requirements, functional and physical design, three layers, decisions |
| 7 | L5 | [w0-scope.md](docs/function-list/w0-scope.md) | Use case inventory, features, Won't-have, data, business rules |
| 8 | L5 | [w1-function-list.md](docs/function-list/w1-function-list.md) | Every function with its EARS criterion, split into work items |
| 9 | L5 | [w2-cost.md](docs/function-list/w2-cost.md), [w4-priorities.md](docs/function-list/w4-priorities.md), [w5-handover.md](docs/function-list/w5-handover.md) | Cost, priorities, threshold checks, three scenarios |
| 10 | L6 | [w6-cash-flow.md](docs/function-list/w6-cash-flow.md) | Cash flow, NPV, IRR, payback for the three scenarios |
| 11 | L7 | [activity-index.md](docs/activity/activity-index.md), [AD-UC-01.md](docs/activity/AD-UC-01.md), [AD-UC-05.md](docs/activity/AD-UC-05.md) | Inputs check against L3-L4, then activity diagrams |
| 12 | L8 | [usage-flow.md](docs/external-design/usage-flow.md) | One usage flow per actor, linked to activity diagrams and screens |
| 13 | L8 | [screen-list.md](docs/external-design/screen-list.md), [screen-transition.md](docs/external-design/screen-transition.md), [ui-conventions.md](docs/external-design/ui-conventions.md) | Screens, how users move, shared conventions and design tokens |
| 14 | L8 | [screen-spec-S-F01-02.md](docs/external-design/screens/screen-spec-S-F01-02.md) | One complete Screen Spec: one image per state, numbered image |
| all | all | [ai-log.md](docs/project/ai-log.md) | Where AI suggested something wrong, and what the team did |

**For student teams.** Your own repository follows the same map and the same README sections,
written for your product. The architecture folder is optional in DBIZ2 but encouraged; if you
leave it out, say so in section 7 of your README, and section 3 then has no architecture rows.

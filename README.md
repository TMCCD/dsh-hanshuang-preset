# dsh-hanshuang-preset

A **DeepSeek Harness (dsh) profile bundle** that registers an independent agent preset named `hanshuang` (display name **Hanshuang**). The protocol clauses are injected through the `persona` plugin at the **system-prompt layer** — they do not travel through the AGENTS.md file / user-message channel, so there is no workspace-instructions preamble and no 64 KB instruction truncation.

## What it contains

| Item | Value |
| --- | --- |
| Preset id | `hanshuang` |
| Row id | `preset-hanshuang` |
| Order | `2` |
| Plugins | 22 — persona + 21 standard tool/group plugins |
| Instructions channel | persona prefix → system prompt |
| Runtime dependencies | none (declarative patch only) |

The preset mirrors the standard desktop plugin set, with the workspace `agent-instructions` plugin omitted on purpose; clauses live in the persona prefix instead.

## Files

```
hanshuang-preset/
├── package.json        # bundle manifest (dsh.bundle.patch points at the patch file)
├── cordis.patch.yml    # cordis overlay patch: the preset row + plugin list
├── LICENSE
└── README.md
```

## Install

From the dsh plugin manager, install the git source:

```
github:TMCCD/dsh-hanshuang-preset
```

or the HTTPS repository URL:

```
https://github.com/TMCCD/dsh-hanshuang-preset.git
```

dsh resolves the bundle, copies it under the profile `node_modules`, and appends the package name to `dsh.profile.bundles` in the profile `package.json`.

## Select the preset

Open a **new** dsh session and pick **Hanshuang** in the preset selector. Existing sessions keep the preset they started with.

## Uninstall

- Remove the package with the dsh plugin manager, or
- delete the package directory from the profile `node_modules` and remove its name from both `dependencies` and `dsh.profile.bundles` in the profile `package.json`.

## Compatibility

- Declarative profile bundle for the dsh desktop profile.
- No build step, no compiled code, no peer runtime packages required beyond what the standard dsh installation already provides.

## Version

`1.0.0` — first published bundle.

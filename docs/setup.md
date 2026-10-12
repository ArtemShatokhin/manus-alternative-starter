# Set up the open-source Kortix starter

Kortix is the open-source AI Operating System, and this page takes the research starter from a fresh terminal to a merged change request. Every step is a git operation on the project repository.

## Before you start

- The `kortix` CLI. Install it with one command.
- A Kortix account. `kortix login` creates one or signs you in.
- A git client.

## Install the open-source CLI

```bash
curl -fsSL https://kortix.com/install | bash
```

The installer supports macOS and Linux on x86_64 and arm64. On Windows, run it inside WSL. It installs the `kortix` command and the `kortixt` TUI.

## Sign in

```bash
kortix login
```

Your browser opens, you approve the CLI, and the token returns to the terminal. If you belong to several accounts, the CLI asks which one to use. On a machine without a browser, sign in with a personal access token: `kortix login --token kortix_pat_...`.

## Clone the starter and validate it

```bash
git clone <this-repository-url> manus-alternative-starter
cd manus-alternative-starter
kortix validate
```

`kortix validate` reads `kortix.yaml` and checks the files around it. It exits `0` with no errors and `1` with one or more. The same check runs when you ship and when a change request merges, so a clean run here saves a round trip later.

## Ship the project

```bash
kortix ship
```

The first `kortix ship` creates the Kortix project. With no git remote it creates a Kortix-managed repository; with a GitHub remote it links that repository instead. It validates the manifest, commits, asks for any missing secret values, pushes the current branch, and offers to connect the declared connectors. On this starter that connector is Notion, which the agent uses to store finished briefs.

## Run the first session

```bash
kortix sessions new --wait --prompt "Research the three open-source agent platforms with the most momentum and draft a brief."
```

A session is one unit of agent work. It runs the project's default agent, `research`, in its own isolated sandbox, on its own branch. The `--wait` flag keeps the terminal attached until the turn ends. To talk to the agent interactively, run `kortix chat <session_id>`.

## Review and merge the change request

The agent commits the brief, pushes its branch, and opens a change request. Session work reaches `main` through that change request, and merge is default-deny for agents, so a person reviews the diff.

```bash
kortix cr ls
kortix cr diff 1
kortix cr merge 1
git pull
```

`kortix cr merge 1` merges the first open change request into the default branch. `git pull` brings the merged work into your clone.

## Choose a model

The platform default model runs on every plan. To use your own provider keys, open Customize → Models → Providers in the project, or run `kortix providers set <provider>`. Kortix takes any model provider with your own keys, the ChatGPT plan you already pay for, or a sign-in with your OpenCode Console account.

## Check the setup

```bash
kortix doctor
```

`kortix doctor` checks your login and the project, then starts a throwaway session, waits for its sandbox, sends a ping, and deletes it. It exits `0` when every check passes.

## Troubleshooting

- A missing agent `.md`, a missing tool module, or a skill with no `SKILL.md` blocks `kortix validate`. Create the file the error names.
- A session that runs old config needs `kortix sessions reload <session_id>` after the change reaches the default branch.
- A sandbox needs a model. If a turn cannot start, connect a provider key in Customize → Models.

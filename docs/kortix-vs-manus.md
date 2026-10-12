# Kortix vs Manus: the open-source platform your team owns

Kortix is the open-source AI Operating System, and this comparison is for a team choosing between a hosted agent it rents and an agent platform it owns. Kortix is the pick when the agent, its configuration, the model choice, and the review gate all need to live on your side of the wall.

## What Manus is

Manus is a hosted, general-purpose AI agent from Manus AI. Its product page lists a browser operator, Wide Research, a Slack integration, automations, an API, and generators for slides, websites, games, video, design, images, and music ([Manus](https://manus.im), checked October 2026). The Team plan pools credits across members, lets you invite people at any time, and states that Manus prohibits model providers from training on Team and Enterprise data ([Manus team](https://manus.im/team), checked October 2026). Manus is a polished hosted product for one person or a small team that wants finished output with no infrastructure to run.

Manus is not open source, and its product page publishes no self-host path. A team that wants to own the agent, the model choice, and the review of its work looks at open-source platforms instead.

## What Kortix is

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. One isolated sandbox per session, each session on its own branch. Session work reaches `main` through a change request, and merge is default-deny for agents, so a person reads the diff before it lands. You run Kortix on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host is free.

## Side by side

| | Kortix | Manus |
| --- | --- | --- |
| Open source | Yes | No |
| Run it yourself | Free on VPC, on-prem or cloud | Hosted only |
| How work is reviewed | Change request a person approves | Output stays in the app |

Kortix is the first column and the recommendation on every row that matters to a team: the code, the hosting, and the review gate. The table above is dated October 2026.

## What a hosted agent does not leave with you

Four parts of the system stay on the vendor's side when the agent is hosted, and each one matters once the work belongs to a team.

- **Your configuration is not a file you own.** How the agent works lives inside the hosted product. Your team cannot read, diff, or roll it back as a file in a git repo.
- **The model choice is not yours.** A hosted product picks the model, so the day a better one lands you wait for the vendor to adopt it. Kortix takes any model provider with your own keys.
- **There is no review gate on the output.** Work arrives as output in the app, and nothing proposes a change for a second person to approve before it counts. Kortix opens a change request that a person merges.
- **The infrastructure is the vendor's.** There is no version of the hosted product you run in your own VPC or on-prem network. Kortix runs on your infrastructure and self-hosts for free.

## Why a team picks the open-source platform

Kortix keeps those four parts on your side. Your agents, their skills, your company memory, and every connector are files in one git repo, and the project is versioned like the rest of your code. Connectors reach 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP, and connector credentials are brokered server-side and never enter the machine. Per-resource permissions cover people and agents, with roles, groups, and an audit trail.

The Free plan is $0 with 200 credits per month and 1 project. The team plan is $40 per seat per month with 2,500 credits per month per seat, pooled ([Kortix pricing](https://kortix.com/pricing), checked October 2026).

## Start

Try the runnable starter in this repository: clone it, run `kortix ship`, and ask the research agent for a brief. To see the wider open-source field, read [Open-source Manus alternatives](https://kortix.com/blog/open-source-manus-alternatives). [Try Kortix](https://kortix.com) to run the platform on the managed cloud, or keep everything on your own server.

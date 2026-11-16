# Template 6: Spend controls for agent teams

## Use it when
Agents can start paid services, rented machines or metered data, and may run unattended.

## The idea
Nothing that costs money starts without an approved request. The block is enforced by the tooling, not by asking the agent to behave.

## The request
An agent that wants to spend files a short request with:
1. What it wants to buy or run, and why.
2. The decision the spending serves.
3. The expected cost, taken from a small pilot.
4. Cheaper alternatives considered.
5. A hard cap, and what shuts the spending off automatically when it is reached.
6. A deadline after which the approval lapses.

## Enforcement
- A hook in the agent's tooling recognises commands that start paid resources and blocks them unless a matching approved request exists.
- The owner approves or denies. The agent carries on with other work while it waits.
- Every request, decision and actual cost goes into a record.

## Report
- Requests filed, approved, denied and lapsed.
- Approved cap against actual spend for each.
- Anything that ran without approval, and how it got through.

## Rules
- Keys for paid services are held where agents cannot read them and are used only by approved jobs.
- An approval covers one purpose. A new purpose needs a new request.
- Recurring subscriptions get a reminder before each renewal.
- Review denied and lapsed requests. They show what agents want to do when left alone.

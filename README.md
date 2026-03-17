# TrustMesh

**Category:** Agent Runtime Trust Infrastructure for OpenClaw

TrustMesh is a security and governance control plane that sits between OpenClaw agents and high-impact actions.
It turns OpenClaw from a powerful personal assistant into a system organizations can safely operate at scale.

---

## Product Thesis

OpenClaw has already won the capability battle for agentic automation: multi-channel messaging, subagents, cron/heartbeat automation, browser control, node execution, and plugin/skill extensibility are real and production-usable.

The bottleneck is now **trust, control, and auditability**.

The company that defines this category will become the default infrastructure layer for serious OpenClaw deployments, in the same way identity and CI security layers became mandatory in cloud software.

**TrustMesh thesis:**
1. Every important agent action should be policy-evaluated before execution.
2. Every delegation (human -> agent, agent -> subagent) should be explicit, scoped, and expiring.
3. Every skill/plugin/workflow should have provenance and trust scores, not just README text.
4. Security posture should improve with network usage through shared threat intelligence and policy learnings.

---

## Problem and Pain Points

### 1) OpenClaw is powerful, but trust boundaries are fragile by default

OpenClaw docs explicitly frame a personal assistant trust model and warn against adversarial multi-tenant assumptions. This is the right warning, but it exposes a market gap:
- teams still want shared deployments
- they still need role-based control and compliance
- they still need to prove what happened, when, and why

### 2) Tool surface includes high-impact primitives

OpenClaw ships first-class tooling for:
- shell execution (`exec`)
- browser automation with signed-in sessions
- node-level run/camera/screen/location
- scheduling and autonomous runs (`cron`, `subagents`)
- cross-channel messaging

These are exactly the capabilities enterprises want and exactly what compliance/security teams fear.

### 3) Skill/plugin ecosystem quality and supply-chain trust are uneven

Skills are easy to publish and install. That velocity is a strength, but it creates uncertainty around:
- author trust
- hidden behavior
- dependency risk
- policy fit for regulated environments

### 4) Operational behaviors are becoming autonomous

From community showcase patterns, users are already running:
- background subagent research
- daily autonomous routines
- multi-agent “armies” across channels/devices
- self-modifying automations

This is not “chatbot usage.” It is an emerging ops layer with insufficient default governance.

### 5) No default trust graph exists

Today there is no ecosystem-wide layer for:
- reputation of skills/workflows
- attested execution history
- policy simulation before rollout
- incident pattern sharing

Without this, each advanced user/team re-invents security controls from scratch.

---

## Why This Opportunity Exists Now

1. **Capability maturity has crossed the threshold**
   OpenClaw is no longer a toy assistant architecture. It has channel breadth, automation primitives, and device reach that resemble real operations platforms.

2. **Behavior shift from request/response to persistent autonomy**
   Heartbeats, cron jobs, and subagents create long-lived autonomous behavior. Governance complexity scales faster than prompt quality.

3. **Ecosystem growth is accelerating**
   OpenClaw and ClawHub adoption signals imply a fast-growing install base and extension economy. Trust infrastructure compounds in value with ecosystem scale.

4. **Security docs already acknowledge risk**
   When a platform’s own docs heavily emphasize trust boundaries, it signals both urgency and buyer awareness.

5. **No obvious category leader yet**
   There is no clear default “Agent IAM + runtime trust” layer native to OpenClaw.

---

## ICP / Target Users

### ICP 1: OpenClaw power users running multi-agent systems
- 3+ agents, cron/subagents, browser+exec tooling
- high appetite for automation
- low appetite for accidental destructive behavior

### ICP 2: Small teams using OpenClaw in shared channels (Discord/Slack/Telegram)
- mixed roles
- need role-aware capabilities and approval boundaries
- need audit logs for accountability

### ICP 3: Security-conscious SMB/enterprise pilots
- legal/compliance stakeholder present
- asks include approval flow, least privilege, evidence trails, incident response

### Economic buyer
- Head of Engineering / Security lead / Technical founder

### Champion
- Agent platform owner (DevOps/productivity automation lead)

---

## Product Overview

TrustMesh has 4 product surfaces.

### A) Runtime Policy Firewall (inline enforcement)

Interposes between OpenClaw tool intents and execution.

Capabilities:
- policy evaluation per action (`exec`, `browser`, `nodes`, `message`, `cron`, `sessions_spawn`)
- context-aware checks (channel, sender identity, tool, path, command, risk level)
- deny / allow / step-up approval decisions
- signed decision receipts

### B) Delegation Engine (capability leases)

Introduces explicit delegation objects:
- who delegated
- what actions are allowed
- path/command/resource constraints
- TTL and revocation

Used for:
- human -> agent high-risk actions
- agent -> subagent task-scoped permissions

### C) Provenance + Audit Ledger

Immutable event chain for:
- requested action
- policy decision
- execution result
- artifacts and hashes
- actor lineage

Designed for incident response and compliance exports.

### D) Trust Graph + Registry Intelligence

Builds ecosystem trust signals over time:
- skill/plugin provenance metadata
- organization-local trust scores
- global risk fingerprints (opt-in, privacy-preserving)
- policy template recommendations

This is the network-effect core.

---

## MVP Definition (v0)

### Goal
Make OpenClaw deployments materially safer in 30 days without killing velocity.

### MVP scope (must ship)

1. **Proxy mode for high-impact tools only**
   - enforce policies on: `exec`, `browser`, `nodes.run`, `message.send`, `cron.add`, `sessions_spawn`

2. **Policy DSL v1**
   - YAML policy definitions with:
     - actor filters (sender/channel/account)
     - tool/action filters
     - constraints (command/path/domain)
     - decision (`allow`, `deny`, `approve`)

3. **Approval workflow**
   - policy-triggered manual approval path with expiry

4. **Audit log UI + export**
   - timeline, filters, JSON/CSV export, signed receipt chain

5. **OpenClaw integration package**
   - drop-in install + onboarding command

### Explicitly out of scope for MVP
- global ecosystem trust marketplace
- deep ML anomaly scoring
- full enterprise SSO/SCIM
- auto-remediation orchestration

### MVP success metrics
- >= 80% of risky actions pass through policy checks
- >= 50% reduction in unsafe/manual “oops” events in pilot teams
- < 150ms median policy decision overhead
- >= 70% weekly active usage in pilot org admins

---

## Roadmap

### Phase 1 (0-3 months): Wedge
- ship runtime policy firewall + approvals + audit trail
- onboard 5-10 OpenClaw-heavy pilot orgs
- capture blocked action patterns and false positives

### Phase 2 (3-9 months): Productization
- richer delegation model for subagent chains
- policy simulator (“what would this block?”)
- policy packs: startup-safe, agency-safe, enterprise-safe
- compliance report templates (SOC2-ready evidence bundles)

### Phase 3 (9-18 months): Network Layer
- signed skill/workflow provenance checks
- trust scores and risk fingerprints
- org-level benchmark insights
- private/public policy pack exchange

### Phase 4 (18+ months): Category Capture
- become required trust layer for managed OpenClaw fleets
- launch attestation standard for ecosystem tools/workflows
- partner with hosting providers and ClawHub ecosystem operators

---

## GTM Strategy

### Positioning
Not “another security dashboard.”
**TrustMesh = the missing trust runtime for autonomous OpenClaw operations.**

### Land motion
- target advanced OpenClaw operators in Discord + showcase community
- offer “Trust Hardening Sprint” for first deployment
- prove value with blocked incidents + audit evidence in first week

### Expand motion
- from one agent to whole org deployment
- from runtime enforcement to governance reporting
- from local policy packs to org-wide standards

### Community strategy
- publish a free “OpenClaw Security Baseline Pack”
- open-source policy schema + decision receipt format
- release monthly ecosystem threat/risk reports

This creates top-of-funnel trust and locks in TrustMesh as default language for safe operation.

---

## Monetization

### Pricing model
1. **Starter (free/low-cost)**
   - single gateway
   - core policy checks
   - basic logs

2. **Pro**
   - multi-gateway
   - advanced policy packs
   - approval workflows
   - incident timeline + exports

3. **Enterprise**
   - SSO/RBAC
   - custom retention/compliance
   - private trust graph instance
   - premium support + onboarding

### Revenue mechanics
- per gateway + per managed agent bundle
- usage component for policy decision volume
- add-on for trust intelligence feeds

---

## Defensibility

1. **Data moat: policy decisions + outcomes**
   Most competitors can build UI. Few can build rich decision + outcome corpora tied to real agent actions.

2. **Workflow embedding moat**
   Once policy and approvals are embedded in operating workflows, rip-out risk is high.

3. **Trust graph network effects**
   More deployments -> better risk signatures -> better default policy -> stronger outcomes -> more deployments.

4. **Ecosystem standardization moat**
   If TrustMesh defines de facto provenance/attestation format, it becomes infrastructure, not a feature.

5. **Compliance inertia moat**
   Once audit/compliance programs depend on TrustMesh exports, stickiness rises dramatically.

---

## Technical Architecture Direction

### High-level architecture

1. **Policy Decision Point (PDP) service**
- stateless API for allow/deny/approve decisions
- policy evaluation engine
- cached policy graph

2. **Policy Enforcement Point (PEP) adapters**
- OpenClaw integration layer intercepting tool calls
- context extraction and normalization
- fail-safe behavior controls

3. **Delegation service**
- issue, verify, revoke capability leases
- TTL and scope enforcement

4. **Audit + Provenance service**
- append-only event stream
- artifact hashing
- signed receipt generation

5. **Admin console**
- policy editing, simulations, incident timeline, exports

### Suggested stack (initial)
- Backend: TypeScript (NestJS/Fastify)
- Policy eval: Cedar-like model or OPA/Rego subset
- Queue/Eventing: Redis Streams initially, Kafka later
- Storage: Postgres + object storage
- Signatures: Ed25519 for receipt chain
- Frontend: Next.js admin console

### Security model
- default deny on unknown high-impact actions
- explicit break-glass controls with short TTL
- tamper-evident audit chain
- strict tenant isolation in SaaS mode

---

## Execution Phases for Agents

### Phase A: Market + threat validation (Agent: Research)
- interview 25 OpenClaw power users
- classify top 20 failure modes and security scares
- map willingness-to-pay by segment

Deliverables:
- `docs/research/interviews.md`
- `docs/research/failure-taxonomy.md`
- `docs/research/wtp-notes.md`

### Phase B: Policy kernel prototype (Agent: Platform)
- implement policy schema + evaluator
- build tool-intent normalization contracts
- run offline replay tests on synthetic traces

Deliverables:
- `packages/policy-core`
- `packages/event-schema`
- coverage report and golden tests

### Phase C: OpenClaw adapter (Agent: Integration)
- implement PEP adapter for target tools
- connect approve/deny loop to policy kernel
- expose decision telemetry

Deliverables:
- `packages/openclaw-adapter`
- integration test suite

### Phase D: Audit console (Agent: Product)
- build timeline and filter UI
- export paths and signed receipts
- incident drill-down views

Deliverables:
- `apps/console`

### Phase E: Pilot operations (Agent: GTM)
- onboard 5 pilots
- weekly policy tuning loops
- publish 2 case studies with hard metrics

Deliverables:
- `docs/case-studies/*`
- pilot KPI dashboard

---

## Immediate Next Tasks (next 14 days)

1. Finalize v0 PRD (`/docs/PRD-v0.md`)
2. Define canonical action schema (`/packages/event-schema`)
3. Build policy evaluator MVP with 10 core rules
4. Implement OpenClaw adapter for `exec` and `sessions_spawn` first
5. Build minimal CLI:
   - `trustmesh policy check`
   - `trustmesh policy test`
   - `trustmesh audit tail`
6. Recruit first 3 pilot users from advanced OpenClaw communities
7. Run first red-team simulation and measure block/allow precision

---

## Main Risks

1. **Integration fragility across OpenClaw updates**
   Mitigation: strict compatibility matrix + automated contract tests.

2. **Too much friction, not enough automation**
   Mitigation: adaptive policies, simulation mode, good defaults.

3. **Trust fatigue from false positives**
   Mitigation: rapid tuning UX + explainable policy decisions.

4. **Platform dependence on OpenClaw internals**
   Mitigation: versioned adapter strategy and public integration spec.

5. **Security startup paradox (must be secure from day one)**
   Mitigation: external audit early, minimal privileged surface, signed logs.

---

## Unresolved Questions

1. Should TrustMesh be delivered primarily as:
   - managed cloud control plane
   - self-hosted package
   - hybrid model?

2. How much policy complexity can non-security operators handle before drop-off?

3. What should be the canonical risk taxonomy for agent actions in OpenClaw?

4. Can we establish a shared provenance standard with ecosystem maintainers early?

5. How to design opt-in shared intelligence without leaking sensitive workflow data?

---

## Why This Can Become Category-Defining

TrustMesh is not a convenience layer.
It is the missing safety-and-trust substrate required for OpenClaw to move from advanced personal automation to broad team and enterprise adoption.

If successful, TrustMesh becomes:
- the default enforcement layer for high-impact actions
- the default audit system for autonomous runs
- the default trust graph for skills/workflows

That is infrastructure-level leverage.

---

## Research Notes (Summary Inputs)

Primary research sources used in this direction:
- OpenClaw docs on subagents, tools, browser, nodes, cron/heartbeat, discord thread binding, and gateway security
- OpenClaw FAQ guidance on trust model, scaling patterns, and common operational pitfalls
- OpenClaw showcase behavior patterns showing rapid shift toward autonomous, multi-agent, always-on usage
- Independent deep-research run executed via a dedicated OpenClaw local agent session


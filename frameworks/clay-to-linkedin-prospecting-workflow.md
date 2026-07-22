# Clay-to-LinkedIn Prospecting Workflow

Build a reviewable workflow from account selection to a useful LinkedIn action. This framework does not include cold email.

## Outcome

The final output is a queue where every record has:

- A clear fit decision
- The evidence behind that decision
- A current LinkedIn-relevant signal or relationship context
- One next action, including no action
- An owner and due date
- A source link
- An outcome that can improve the rules

## System map

```text
ICP definition
  -> account sources
  -> account gate
  -> person selection
  -> conditional enrichment
  -> fit and confidence scoring
  -> LinkedIn signal review
  -> action routing
  -> human approval
  -> outcome logging
  -> weekly rule update
```

## Stage 1: Define fit before opening Clay

Write the rules in plain language first.

### Account fit

- Industry or use case
- Company size or operating complexity
- Geography
- Business model
- Relevant technology or process
- Trigger or timing condition
- Hard disqualifiers

### Person fit

- Buying role
- Seniority
- Function
- Responsibility connected to the problem
- Influence or decision authority
- Hard disqualifiers

### Evidence rules

For every criterion, define:

- Accepted source
- Freshness window
- What counts as unknown
- Whether the criterion is required, weighted, or informational
- Whether conflicting sources require review

Use the [LinkedIn ICP Finder](https://www.promiseclick.com/resources/playbooks/linkedin-icp-finder-claude-skill) if the ICP is still a loose list of industries and titles.

## Stage 2: Source accounts first

Start with companies, not a large person list.

Possible sources include:

- LinkedIn Sales Navigator account searches
- CRM customers, opportunities, and disqualifications
- Website or product activity with appropriate consent
- Events, communities, referrals, and partnerships
- Curated industry lists
- Another trusted data source

Keep these fields on import:

| Field | Purpose |
|---|---|
| `source_name` | Identifies the system or list |
| `source_url` | Preserves evidence and reviewability |
| `source_date` | Supports freshness rules |
| `source_context` | Explains why the account entered the workflow |
| `company_name` | Human-readable identity |
| `company_domain` | Primary matching key |
| `company_linkedin_url` | LinkedIn identity |

Normalize domains before deduplication. Keep the original source fields even after enrichment.

## Stage 3: Apply the account gate

Reject or pause obvious non-fits before people enrichment.

Example outcomes:

- `QUALIFIED_ACCOUNT`
- `DISQUALIFIED_ACCOUNT`
- `NEEDS_REVIEW`
- `MISSING_REQUIRED_DATA`

Do not treat missing data as a negative fact. An unknown company size is not the same as a company outside the size range.

## Stage 4: Select people and enrich conditionally

Find people only at accounts that pass the gate.

Minimum person fields:

- Full name
- Current role
- Seniority
- LinkedIn URL
- Likely buying role
- Source and date

Add firmographic, role, profile, and research fields only when they can change a score or action. Use Clay run conditions to prevent expensive steps from running when required inputs are missing or the account is already disqualified.

Test every provider or waterfall on a small sample that includes:

- Strong fits
- Weak fits
- Missing domains
- Duplicate companies
- Ambiguous roles
- Stale profiles
- Conflicting data

Official reference: [Clay enrichments documentation](https://university.clay.com/docs/enrichments).

## Stage 5: Score fit, context, and confidence separately

Do not hide every judgment in one number.

| Score | Range | Question |
|---|---:|---|
| Account fit | 0-40 | Does the company match the operating ICP? |
| Person fit | 0-25 | Is this person connected to the problem and decision? |
| Timing signal | 0-15 | Is there current evidence that the topic matters now? |
| Relationship context | 0-10 | Is there a real reason for a public or private interaction? |
| Data confidence | 0-10 | How complete, current, and consistent is the evidence? |

Store the reason and source beside every score. Use the [LinkedIn Lead Scorer](https://www.promiseclick.com/resources/playbooks/linkedin-lead-scorer-claude-skill) to pressure-test the model and explain disqualifiers.

Suggested routing bands:

- `80-100`: review for a current action
- `65-79`: research or monitor
- `45-64`: nurture only when there is useful context
- `0-44`: no action or disqualify

These bands are starting points. Update them from actual qualified outcomes.

## Stage 6: Detect LinkedIn-relevant signals

Useful signals can include:

- Role change
- Relevant hiring activity
- Company announcement tied to the problem
- A post about the problem, priority, or initiative
- A comment in a relevant discussion
- A shared event, group, customer, or partner context
- Prior accepted connection or conversation

Store:

- Signal type
- Exact source URL
- Observed date
- Expiry date
- Why it matters
- Confidence

A signal is context, not permission to pitch. Remove or expire signals that no longer support a current action.

## Stage 7: Route one next action

Available routes:

| Route | Use when |
|---|---|
| Monitor | Fit is strong but context is weak or timing is unclear |
| Research | One decision-changing fact is missing |
| Connect without note | The person is relevant but a note would add no genuine context |
| Connect with note | A specific, honest reason fits the current interface limit |
| Comment | The person shared something where you can add useful public context |
| Warm DM | A real relationship or interaction supports a private next step |
| Nurture | The account fits but the current action would be premature |
| No action | Fit, confidence, timing, or relationship context is insufficient |

Every route should have:

- Action reason
- Source URL
- Human owner
- Review status
- Due date
- Expiry date
- Outcome

Use the [LinkedIn Connection Request Writer](https://www.promiseclick.com/resources/playbooks/linkedin-connection-request-writer) before connecting, and the [LinkedIn Comment-to-DM Bridge](https://www.promiseclick.com/resources/playbooks/linkedin-comment-to-dm-bridge) when a public interaction may justify a private message.

## Quality and cost controls

- Filter accounts before people enrichment.
- Run only decision-changing fields.
- Use conditions for missing inputs and failed gates.
- Stop a waterfall after sufficient confidence.
- Preserve unknown values instead of guessing.
- Expire stale signals.
- Deduplicate by stable company and person identifiers.
- Require human approval for messages and public claims.
- Track credits per accepted account and qualified person.
- Keep a suppression list for disqualified, opted-out, or unsafe records.

## Weekly learning loop

Review:

1. Qualified records accepted by the team
2. False positives and false negatives
3. Replies that became useful conversations
4. Disqualification reasons
5. Stale or misleading signals
6. Enrichments that never changed a decision
7. Credits per accepted record
8. Rules that need one controlled update

Change one rule at a time when possible. Record the old rule, new rule, reason, date, and expected effect.

## Launch checklist

- [ ] ICP and disqualifiers are written.
- [ ] Accepted sources and freshness windows are defined.
- [ ] Account gate runs before person enrichment.
- [ ] Required fields and unknown states are explicit.
- [ ] Score components and reasons are visible.
- [ ] Signals include source and expiry dates.
- [ ] Every action has a human owner.
- [ ] No action is an available route.
- [ ] A mixed sample has passed QA.
- [ ] Credit and outcome reporting is active.
- [ ] Suppression and privacy rules are documented.

## Related resources

- [Clay review](https://www.promiseclick.com/resources/tools/clay)
- [LinkedIn Sales Navigator review](https://www.promiseclick.com/resources/tools/linkedin-sales-navigator)
- [LinkedIn Pipeline Tool Stack](https://www.promiseclick.com/resources/playbooks/linkedin-pipeline-tool-stack)
- [How to Use Clay for B2B Prospecting](https://www.promiseclick.com/blog/how-to-use-clay-guide-b2b)

---

Created by [PromiseClick](https://www.promiseclick.com). Licensed CC BY 4.0.

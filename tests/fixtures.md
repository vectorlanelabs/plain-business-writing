# Fixtures

Twenty cases in four groups of five: good text that must stay, semantic drift traps, obvious slop, and borderline cases. See [README.md](README.md) for criteria and how to run.

Each case lists the audience and medium, the source text, the expected action, invariants that must survive, and unacceptable outcomes. Candidates marked Acceptable are examples of good output. Candidates marked Control are for blind comparison and may fail.

## Good text (expected action: Retain)

### G1. Internal update email
- **Audience:** team, email
- **Source:** "Hi team, the March close finished Thursday, a day late. The delay came from two unmatched bank deposits, which Priya cleared on Wednesday. April should close on time."
- **Invariants:** finished Thursday, one day late, two unmatched deposits cleared Wednesday, April outlook.
- **Unacceptable:** any rewrite that changes wording without fixing a problem, or softens "should".

### G2. Technical note
- **Audience:** customers, help article
- **Source:** "The sync runs hourly. If a reservation changes between runs, the change shows up in the next run."
- **Invariants:** hourly schedule, change appears on the next run.
- **Unacceptable:** merging into one sentence for rhythm alone, or adding a claim about timing guarantees.

### G3. Customer email with distinct short sentences
- **Audience:** customer, email
- **Source:** "Your export is ready. It has 14,200 rows and covers January through June. If a column looks wrong, reply to this email and we'll fix it today."
- **Invariants:** row count, date range, same day fix offer.
- **Unacceptable:** treating this as a staccato stack. Each sentence carries a different fact or action.

### G4. Slide title and card labels
- **Audience:** executives, slide
- **Source:** Title "Q3 churn by segment" with card labels "Enterprise: 2.1%", "Mid market: 3.4%", "Small: 5.0%".
- **Invariants:** all three figures and labels.
- **Unacceptable:** rewriting fragments into sentences. Titles and short labels may be fragments.

### G5. Blunt voice, multiple sentences
- **Audience:** leadership, internal note
- **Source:** "We missed the launch date by three weeks. The vendor slipped twice and we believed them both times, which was our mistake. The new date is June 12 and I'd bet on it."
- **Invariants:** three weeks, vendor slipped twice, ownership of the mistake, June 12, the writer's confidence.
- **Unacceptable:** sanding the opinion into neutral language, or removing "I'd bet on it".

## Semantic drift traps

### D1. Uncertainty
- **Audience:** advisory board, proposal
- **Source:** "It's not that the overlay route is broken, it's that we simply don't know yet whether it holds up across brands."
- **Expected action:** Edit
- **Invariants:** the claim is untested. No statement that it works or that it fails.
- **Unacceptable:** "The overlay route holds up across brands." or "The overlay route may fail on some brands."
- **Candidate:** "We don't yet know whether the overlay route holds up across brands."

### D2. Causality
- **Audience:** executives, report
- **Source:** "Occupancy rose 4% after the price change, highlighting the pricing's impact. Two large groups also booked that month, so we can't yet separate the two."
- **Expected action:** Edit
- **Invariants:** 4%, timing, the two groups, the stated inability to separate causes.
- **Unacceptable:** stating that the price change caused the rise, or dropping the groups.
- **Candidate:** "Occupancy rose 4% after the price change. Two large groups also booked that month, so we can't yet say how much the price change contributed."

### D3. Product boundary (two variants)
- **Source:** "This isn't a reporting tool. It's a control layer."
- **Invariants:** it is a control layer. Nothing about reporting is added or claimed beyond the source.
- **Unacceptable in both variants:** "a control layer that also reports", or any new capability.
- **Variant A, context given:** the audience has just seen a reporting dashboard and may take this for one. Expected action: Retain. The negative half excludes a plausible reading. Edit passes only if the exclusion survives, for example "This is a control layer, not a reporting tool."
- **Variant B, no context:** the audience has no reason to expect a reporting tool. Expected action: Edit. "This is a control layer." passes. Retaining fails unless the grader finds a stated reason in the text.
- **Note:** the grader receives the variant's context and may not supply their own.

### D4. Numbers and attribution
- **Audience:** customers, case study
- **Source:** "The pilot, which ran at 12 properties from March to May, cut check in time by 18%, a result the Harbor Group team called remarkable."
- **Expected action:** Edit
- **Invariants:** 12 properties, March to May, 18%, Harbor Group, the word "remarkable" attributed to them.
- **Unacceptable:** changing any figure, removing the attribution, or presenting "remarkable" as the writer's own claim.
- **Candidate:** "The pilot ran at 12 properties from March to May and cut check in time by 18%. The Harbor Group team called the result remarkable."

### D5. Asymmetry
- **Audience:** partners, proposal
- **Source:** "We're not giving both apps a facelift. The mobile app gets a full rebuild, and the web app gets new screens on the existing backend."
- **Expected action:** Borderline. Retain or Edit.
- **Invariants:** the mobile app is fully rebuilt. The web app gets new screens only, on the existing backend.
- **Unacceptable:** any version saying both apps are rebuilt, or both are refreshed.
- **Retain passes if** the contrast is kept because it excludes the reading that both apps get the same treatment. **Edit passes if** the asymmetry survives in plain wording.

## Obvious slop (expected action: Edit)

### S1. Staccato subtitle
- **Audience:** advisory board, title slide
- **Source:** "A proposal and a working concept. The name is a placeholder. We want you to help us pick it apart."
- **Invariants:** the document is provisional, the name is provisional, criticism is invited. The phrase "pick it apart" should survive unless there is a reason.
- **Unacceptable:** dropping any of the three facts, flattening "pick it apart" to "feedback", or adding a new claim.
- **Acceptable:** "This is a working proposal, and the name is still a placeholder. We'd like you to pick it apart."
- **Control (may fail voice):** "This is a proposal and a working concept, and the name is a placeholder we want your feedback on."
- **Note:** both versions go into the blind comparison. The control weakens \"pick it apart\" to \"feedback\" and is expected to rate lower on voice.

### S2. Chatbot residue and buzzwords
- **Audience:** prospect, email
- **Source:** "Great question! Here's the thing: our onboarding isn't just fast, it's robust and seamless. Most properties go live in 22 days. Let me know if you'd like me to walk you through it. Hope this helps!"
- **Invariants:** most properties go live in 22 days. An offer to walk through it may stay.
- **Unacceptable:** inventing a speed claim, a guarantee or a comparison.
- **Candidate:** "Most properties go live in 22 days. I'm happy to walk you through the process."

### S3. Content free build up
- **Audience:** advisory board, proposal opening
- **Source:** "Hotels run on data. But data alone isn't enough. What nobody tells you is that the real gap is action. That's where we come in."
- **Invariants:** the only supported idea is that hotels have data and lack ways to act on it.
- **Unacceptable:** inventing statistics, a study or a named customer. Replacing the build up with a new punchy line.
- **Candidate:** "Hotels have plenty of data and few ways to act on it."

### S4. Markup with triad, dashes and bold labels
- **Audience:** customers, release notes
- **Source:**
  ```
  ## Benefits

  Benefits of the new dashboard — faster, simpler, smarter:

  - **Speed:** loads in under 2 seconds
  - **Simplicity:** one screen for all properties
  - **Smarts:** flags unusual spend
  ```
- **Invariants:** under 2 seconds, one screen for all properties, flags unusual spend.
- **Unacceptable:** adding a fourth benefit, changing the 2 second figure, keeping the "faster, simpler, smarter" framing, keeping the dash, or repeating the heading in the first line.
- **Acceptable:** "The new dashboard loads in under 2 seconds, shows all properties on one screen and flags unusual spend."
- **Also acceptable:** the same three facts as a short labeled list without the framing line. Labeled bullets can be the clearest way to scan release notes, so removing them is not required. That is a house style choice and is scored separately.

### S5. Borrowed authority and sales language
- **Audience:** prospects, web copy
- **Source:** "Industry experts agree that our groundbreaking platform isn't just software, it's a partnership. Studies show hotels see stunning results."
- **Invariants:** no supported facts exist beyond what the platform is. No source or figure is available.
- **Unacceptable:** inventing a source, a figure or a result.
- **Expected output:** remove the borrowed authority and sales claims, and flag that no factual basis was supplied, for example with a placeholder such as [what the platform does, with a source for any result]. The output must not describe the platform beyond what the source states.

## Borderline cases

### B1. Deliberate short run
- **Audience:** leadership, internal note
- **Source:** "We tried it twice. It failed twice. We stopped."
- **Expected action:** Retain or Edit
- **Invariants:** two attempts, two failures, the decision to stop.
- **Unacceptable:** adding a reason for the failures or a lesson learned.
- **Candidate edit:** "We tried it twice, it failed both times, and we stopped."
- **Retain passes if** the reason is the writer's voice and the three facts are untouched. **Edit passes if** the candidate keeps all three facts without adding a reason or lesson. Neither passes without a stated reason.

### B2. Real triad
- **Audience:** customers, packing list
- **Source:** "The kit includes a key card encoder, a card printer and a spare set of cables."
- **Expected action:** Retain
- **Invariants:** three distinct items.
- **Unacceptable:** dropping or merging any item, or adding one.
- **Note:** three items here are three distinct things, so this is not a forced triad.

### B3. Writing sample overrides the dash rule
- **Audience:** internal note
- **Writing sample:** "We shipped Friday — late, but clean."
- **Source to edit:** "The fix landed Monday — one day late, but it held."
- **Expected action:** Retain the dash
- **Invariants:** landed Monday, one day late, it held.
- **Unacceptable:** removing the dash only to satisfy the no dash house style when the sample shows the author uses one.
- **Note:** one sample sentence shows compatible punctuation is allowed. It does not make dashes a requirement, and the edit may restructure the sentence if it reads better. Scored under house style.

### B4. Contrast that prevents a misreading
- **Audience:** customer, standalone message
- **Source:** "This is not a refund. It is a credit against your next invoice."
- **Expected action:** Retain
- **Invariants:** the exclusion of a refund, the credit against the next invoice.
- **Unacceptable:** "This is a credit against your next invoice." if the customer may reasonably expect a refund.
- **Note:** the negative half excludes a plausible reading the positive half does not reliably exclude.

### B5. Parallel sentences with distinct facts
- **Audience:** prospects, web copy
- **Source:** "Our onboarding takes 22 days on average. Our support wait is under 3 minutes. Our integrations number more than 30."
- **Expected action:** Retain or Edit
- **Invariants:** 22 days average, under 3 minutes, more than 30 integrations.
- **Unacceptable:** dropping a figure, rounding any of them, or adding a claim about quality.
- **Acceptable edit:** "Onboarding takes 22 days on average, the support wait is under 3 minutes and we offer more than 30 integrations."
- **Note:** repeated openings are a tell, but each sentence carries a different number. Retain passes if the grader accepts that each sentence carries a different number. Edit passes only if all three figures and the wait time metric survive exactly.

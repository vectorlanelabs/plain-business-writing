# Tests

These fixtures check that the skill improves writing without damaging it. They come out of the discussion on issue 1 and are meant to settle wording questions with evidence.

## Order of authority

When rules conflict, the higher item wins.

1. Meaning and facts
2. Voice and passage level naturalness
3. Pattern removal
4. House style

## How to run

1. Give the skill and one fixture's source text to the model under test, in Edit mode unless the fixture says otherwise.
2. Collect the output.
3. Grade it against the fixture's invariants and unacceptable outcomes. The model that wrote the output must not be its only grader. Use a different model or a human, ideally blind to which version of the skill produced it.
4. Record the result using the criteria below.

Fixtures do not require one exact output. Candidates marked Acceptable are examples of good results, not answers to match. Candidates marked Control are for blind comparison and may fail.

## Criteria

**Hard fail**
- Invents a fact or capability.
- Changes certainty or causality.
- Loses a material distinction.
- Alters a quote, name or number.

**Fail**
- Flattens the author's voice.
- Produces a less natural passage.
- Changes already good writing without need.
- Leaves obvious sloppy construction when a clearly better, faithful rewrite is available.
- Replaces a removed pattern with another tell, such as a colon reveal, a semicolon or a new punchy structure.

**Pass**
- Removes distracting patterns while keeping meaning, voice and readability.
- Keeps an apparent pattern when removing it would weaken meaning, voice or naturalness.

House style (no dashes, tagline rules) is scored separately and never outranks the items above.

## Baseline and repeat runs

1. Before changing `SKILL.md`, run the current skill on every fixture and save the outputs as the baseline. The baseline is the `SKILL.md` at commit `2a4cd7f`.
2. Run the revised skill on the same inputs and compare.
3. Repeat each fixture several times. A skill that passes once and fails the next run is inconsistent, and a single good output proves little.

## Scoring

Report objective fidelity failures separately from subjective judgments. A changed number, an invented capability or a shifted certainty is counted as a hard fail and is never averaged against style ratings. Voice and naturalness are rated separately, blind where possible.

## Metrics

Track these separately across a run.

- Semantic drift: count of hard fails.
- Unnecessary edits: edits to cases marked Retain.
- Surviving slop: cases marked Edit that came back with the problem intact.

## Borderline cases

A borderline case allows either Retain or Edit. Each fixture states what makes each outcome pass or fail, so "either" never becomes an automatic pass. The chosen action must meet the invariants, and the grader must be able to see a reason for it.

## Notes

- All numbers, names and companies in the source texts are invented test data.
- Source texts include deliberate slop, dashes included, because they are the input being tested.
- Multi-sentence passages are used on purpose. The unit being judged is the passage, not the sentence.

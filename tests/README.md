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

Fixtures do not require one exact output. Candidate rewrites are examples of acceptable results, not answers to match.

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

## Metrics

Track these separately across a run.

- Semantic drift: count of hard fails.
- Unnecessary edits: edits to cases marked Retain.
- Surviving slop: cases marked Edit that came back with the problem intact.

## Borderline cases

A borderline case allows either Retain or Edit. The chosen action only passes if it meets the invariants and the grader can see a reason for it.

## Notes

- All numbers, names and companies in the source texts are invented test data.
- Source texts include deliberate slop, dashes included, because they are the input being tested.
- Multi-sentence passages are used on purpose. The unit being judged is the passage, not the sentence.

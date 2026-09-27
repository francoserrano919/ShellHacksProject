# Stepwise judging walkthrough (about 2 minutes)

## Prepare

- Open the app on your Mac and select **The missing last number**.
- Check the sidebar. To demonstrate AI selection, turn **Offline demo mode** off and have the API key loaded in the launching terminal. To guarantee a smooth demo, turn offline mode on.
- Keep one completed practice report ready as a backup.

## Show the real task

1. **Challenge (15 seconds):** “This code should print 1 through 5, but it stops early. Stepwise asks the student to find why and make the edit.” Point to the code and four stage indicators.
2. **Prediction (20 seconds):** Enter `4` as the original loop's last value, then check the step. The correct-answer bar advances automatically, or click **Continue now**.
3. **Adaptive hint (25 seconds):** At Investigate, write `I think the stop value may be included` in the thinking box and request a hint. Point out the hint source and AI-selected count. The hint asks a question and does not reveal a corrected program.
4. **Revision (25 seconds):** Click the `Excluded` answer choice, change only the upper bound in the editor, and submit the revision. Explain that the student makes the code change.
5. **Transfer (20 seconds):** Show the fresh loop in Try independently. The final stage has no hint button. Complete it and show the report download with thinking, correct answers, and incorrect attempts.
6. **Breadth (15 seconds):** Switch to The boundary case or The disappearing total to show that the same learning flow handles another Python concept.

## One-sentence explanation of AI and guardrails

“Gemini selects from two reviewed prompts based on the learner's thinking; the app checks the ID and displays only approved hint text, while syntax validation checks the student's revision without running their code.”

## If the API is unavailable

Turn on **Offline demo mode**, restart the lesson, and run the same walkthrough with built-in hints. Identify it honestly as the offline path. The AI-selected count remains zero in this mode.

## Scope to describe accurately

The submitted app includes three curated Python lessons. Screenshot input, arbitrary problem generation, and math practice are future directions, not current features.

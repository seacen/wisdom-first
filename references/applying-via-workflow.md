# Applying the framework via a Workflow

Step 3 of the skill — solving the user's problem *through* the chosen framework —
can be done inline in a single response for most consults. But for genuinely heavy
long-horizon work, a multi-agent Workflow produces a more thorough, better-checked
result. This file says when that's worth it and gives a template to adapt.

## When to escalate to a Workflow

Escalate when **all** of these hold:

- The deliverable is large and long-horizon: a full strategy document, a complete
  speech or deck, a board memo, a detailed plan, a design system — not a
  three-paragraph answer.
- The chosen framework has **separable components** that can be worked in parallel
  — most strong frameworks decompose into a handful of distinct parts, steps, or
  moves that can each be developed on their own before being recombined.
- Quality and thoroughness matter more than turnaround.

Do **not** escalate for a quick consult, an emotional conversation, or anything
where a single thoughtful response is plainly enough. Spinning up a fleet of
agents for a small question is the over-framing pitfall in a more expensive form.

## The pattern

The framework you selected becomes the *skeleton of the workflow*:

1. **Frame** — one pass that maps the user's problem onto the framework's
   structure and names each component to be worked.
2. **Decompose and fan out** — one agent per component, each working its piece
   *using the framework's vocabulary for that piece*, in parallel.
3. **Fidelity critique** — an adversarial pass that checks each piece actually
   applied the framework rather than drifting into generic advice (the same
   fidelity test from the skill), and flags weak or off-framework parts.
4. **Synthesize** — assemble the verified pieces into the final deliverable, in
   the framework's logic and the user's voice.

## Template to adapt

This is a starting point — rewrite the framework-specific parts for the actual
framework you selected. Pass the user's problem and the chosen framework in via
`args`.

```javascript
export const meta = {
  name: 'apply-framework',
  description: 'Solve a long-horizon task through a chosen framework, then verify fidelity',
  phases: [
    { title: 'Frame' },
    { title: 'Work components' },
    { title: 'Verify & synthesize' },
  ],
}

// args = { problem: "...", framework: "...", components: ["...", "..."] }
phase('Frame')
const plan = await agent(
  `Map this problem onto the framework's structure. Problem: ${args.problem}\n` +
  `Framework: ${args.framework}\n` +
  `Return the concrete components to work, each as {name, brief}.`,
  { schema: { type: 'object', properties: { components: { type: 'array',
      items: { type: 'object', properties: { name: {type:'string'}, brief: {type:'string'} },
      required: ['name','brief'] } } }, required: ['components'] } }
)

phase('Work components')
const drafted = await pipeline(
  plan.components,
  c => agent(
    `Using the framework "${args.framework}", work this component of the solution.\n` +
    `Component: ${c.name} — ${c.brief}\nProblem context: ${args.problem}\n` +
    `Make the framework's concepts and vocabulary load-bearing, not decorative.`,
    { label: `draft:${c.name}`, phase: 'Work components' }
  ),
  // fidelity critique, per component, as soon as its draft is ready
  (draft, c) => agent(
    `Adversarially check this draft. Did it actually apply "${args.framework}", or ` +
    `is it generic advice with the framework's name sprinkled on? Component: ${c.name}.\n` +
    `Draft:\n${draft}\n` +
    `Return { fidelityOk: boolean, problems: [..], improved: "the fixed version" }.`,
    { label: `verify:${c.name}`, phase: 'Verify & synthesize',
      schema: { type: 'object', properties: { fidelityOk: {type:'boolean'},
        problems: {type:'array', items:{type:'string'}}, improved: {type:'string'} },
        required: ['fidelityOk','improved'] } }
  )
).then(rs => rs.filter(Boolean))

phase('Verify & synthesize')
const final = await agent(
  `Synthesize these verified components into one coherent deliverable for the user, ` +
  `in the logic of "${args.framework}". Components:\n` +
  drafted.map((d,i) => `## ${plan.components[i]?.name}\n${d.improved}`).join('\n\n')
)
return { framework: args.framework, deliverable: final }
```

## Reporting back to the user

When you use a workflow, the user should still see the **Frameworks & reading**
section first (the distillation and book recommendation, written by you, not
buried in agent output), then the synthesized deliverable. The workflow is an
implementation detail of step 3 — it does not replace the human-facing distillation
that is the heart of this skill.

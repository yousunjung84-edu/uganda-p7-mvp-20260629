# Uganda P7 Lesson Deck Design Guide

## Design intent

Create practical classroom slides for Ugandan P7 learners: clear, high-contrast, activity-led, and printable from PDF. Slides should feel like a lesson sequence, not a bullet summary.

## Palette

Use colors inspired by the Uganda flag and school noticeboards:

- Charcoal black: `#111827` for titles and strong contrast.
- Uganda yellow: `#FCD116` for highlights and section markers.
- Uganda red: `#D90000` for emphasis and challenge prompts.
- Leaf green: `#1B7F3A` for practice/activity states.
- Lake blue: `#1D4ED8` for questions and navigation.
- Warm paper: `#FFF7E0` for content cards.
- Soft background: `#F8FAFC` for printable pages.

## Layout rules

- Keep an 8-slide classroom flow: hook, mission, starter, concept, model, practice, activity, exit ticket.
- Use a fixed grid so PDF conversion keeps alignment:
  - top banner: 0.78 in
  - title area: 0.95 in
  - content field: 4.9 in
  - footer: 0.30 in
- Avoid free-floating text. Every student-facing text block sits inside a card, board, route, ticket, or banner.
- Vary the slide form by lesson stage:
  - hook: subject infographic plus opening question.
  - mission: four-step route.
  - starter: think-pair-share columns.
  - concept: content map using the subject visual metaphor.
  - model: worked-example map, not a plain bullet board.
  - practice: question-flow cards with answer lines.
  - activity: group infographic plus share-out box.
  - exit: ticket form with writing lines.
- Every content slide must be infographic-first: the main idea and tasks appear as nodes, callouts, paths, Venn/cycle/map/triangle structures, or answer-flow cards before any list-like text treatment.
- Do not exceed 5 visual nodes per slide.
- Keep each node to one short action or idea, with no visible truncation ellipses.

## Visual language

- Use simple geometric motifs that vary by content:
  - Mathematics: Venn circles, number paths, market counters, operation blocks.
  - English: story path, speech bubbles, vocabulary cards, portfolio folders.
  - Integrated Science: system diagrams, experiment/report cycles, observation panels.
  - Social Studies: map frame, compass, continent/ocean labels, portfolio review grid.
  - Christian Religious Education: trinity triangle, faith timeline, community action cards.
- Infographics are separate artifacts, not embedded into every PPT slide.
- Text in infographics must be rendered by code/SVG, not entrusted to image-generation spelling.

## Typography

- Use Aptos/Arial-compatible sans-serif defaults.
- Titles: 26–30 pt.
- Main prompt: 20–21 pt.
- Card text: 15–17 pt.
- PDF readability is more important than decorative density.

## QA expectations

- PPTX opens with python-pptx.
- PDF conversion preserves card alignment.
- Each lesson has one standalone `infographic.svg` and `infographic_prompt.json`.
- QA passes only when PPTX, PDF, outline, trace, and infographic artifacts are all present.

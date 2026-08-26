# Statistics and Probability Open Question Bank

An open STACK question bank for statistics and probability, structured for use with the [stack-agents-michele](https://github.com/IDEMSInternational) editing pipeline.

## Structure

```
questions/
  <category>/
    <question_name>.xml
  <category>/<subcategory>/
    <question_name>.xml
```

Each `.xml` file wraps a single Moodle question:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<quiz>
<question type="stack">
  ...
</question>
</quiz>
```

Questions were imported from a Moodle bulk XML export. Most are `type="stack"`; a handful of `multichoice`/`matching`/`truefalse` questions were carried over as-is but are not editable by the pipeline's STACK-focused Author agent.

Metadata files (`_logs.md`/`_description.md`) are not present yet — the pipeline auto-migrates a flat `category/name.xml` into `category/name/name.xml` plus companion files the first time someone starts an editing session on it.

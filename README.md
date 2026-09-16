# Statistics and Probability Open Question Bank

An open STACK question bank for statistics and probability, synchronised with the
"STACK for Statistics and Probability" course question bank on
[ecampus.idems.international](https://ecampus.idems.international/course/view.php?id=248)
using [moodle-qbank_gitsync](https://github.com/maths/moodle-qbank_gitsync).

## Structure

```
top/
  <category>/
    <question_name>.xml
    gitsync_category.xml
  <category>/<subcategory>/
    <question_name>.xml
    gitsync_category.xml
```

`top` mirrors the Moodle question category tree for the course. Each `.xml` file wraps a
single Moodle question:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<quiz>
<question type="stack">
  ...
</question>
</quiz>
```

Most questions are `type="stack"`; a handful of `multichoice`/`matching`/`truefalse`
questions are also present as-is. Each category directory below `top` has a
`gitsync_category.xml` file describing that Moodle category; this data is not versioned
in Moodle, so it is not updated automatically on later imports/exports.

## Syncing with Moodle

This repo does not track a manifest file (`*_question_manifest.json`) — it is
instance-specific and stays local, per [moodle-qbank_gitsync](https://github.com/maths/moodle-qbank_gitsync)'s
own conventions (see its `.gitignore` entries). To work with this repo:

1. Set up [moodle-qbank_gitsync](https://github.com/maths/moodle-qbank_gitsync) locally
   (PHP + the CLI scripts), pointed at the `ecampus` Moodle instance.
2. Run `importrepotomoodle.php` after editing questions locally, or
   `exportrepofrommoodle.php` to pull the latest state from Moodle, from this directory.

See that project's docs for the full workflow (`createrepo.md`, `importrepotomoodle.md`,
`exportrepofrommoodle.md`).

# Contributing

Thanks for helping grow **Awesome Weight-Space Programming**!

## What belongs here

Work in which a model (usually an LLM) **reads, edits or writes neural-network weights directly**, without an optimizer doing the work. This includes:

- Papers, preprints and technical reports on WSP
- Code, benchmarks, datasets, checkpoints and demos
- Independent reproductions and well-argued critiques (both are very valuable)
- Background work under *Foundations & Related Fields*, only if it clearly informs WSP

General weight-space learning papers (hypernetworks, neural functionals, and so on) belong in the [existing weight-space-learning lists](https://github.com/Zehong-Wang/Awesome-Weight-Space-Learning) unless they bear directly on WSP.

## Entry format

```markdown
- **Paper Title**: First Author et al. [[arXiv XXXX.XXXXX]](https://arxiv.org/abs/XXXX.XXXXX) [[code]](https://github.com/...)
  One sentence on what is new: the setting, the key result, or the key finding.
```

- Use the **abs** page for arXiv links, not the PDF.
- Keep the summary to **one or two sentences** and write it in your own words. Don't paste the abstract.
- Report numbers as the paper states them. Don't round them up into a headline.
- Put the entry in the most specific section, **newest first**.

## Pull request checklist

- [ ] The link works and points to the canonical source
- [ ] The entry is not a duplicate (search the README first)
- [ ] The format matches the existing entries
- [ ] One resource per PR is preferred, though batches of related preprints are fine

The **Check links** workflow runs on every PR. Please fix any broken links it reports.

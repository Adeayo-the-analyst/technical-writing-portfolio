# Clay Credit System Update — Release Notes
## Portfolio Piece: Breaking Change Documentation

### The Architectural Problem

Clay's March 2026 credit system correction introduced a fundamentally
new pricing architecture, separating platform usage from data purchasing
into two distinct currencies.

The structural problem was not the change itself. It was that the documentation
never prepared users for how the new architecture would behave inside their existing
workflows. Credits are not abstract. They are infrastructure embedded in how users
build, run, and scale their prospecting operations. Ambiguity at that layer is not
a minor inconvenience. It is a direct threat to the user's ability to plan and operate.

The documentation treated a workflow-level disruption as a feature announcement.

### The Pattern Chosen

Constraint-first breaking change release notes, organized around the user's workflow
impact rather than the product's new feature.

Most technical writers documenting this correction would have organized it around what
Clay built. This document is organized around what the user needs to do before their 
next billing cycle. The product's architecture is explained only in service of that
user action. Never for its own sake.

Every structural decision follows from one question: what does this user need to know 
right now to protect the workflow they have already built?

### The Commercial Consequence Prevented

A pricing architecture change that users cannot interpret generates one of two
outcomes. Support tickets from users who are confused. Or silent churn from users
who conclude the product has become unpredictable.

This document is designed to prevent both.

By disclosing the constraint clearly, mapping the impact across specific user cohorts,
and providing a migration path before the user encounters the change in their live workflow,
the document reframes the correction from a disruption into a transparency event.

The product manager reading this should see one thing clearly: a pricing architecture
change, handled with this level of documentation precision, does not have to cost you users.
It can build the trust that retains them.

# Gearset First Deployment — User Guide
## Portfolio Piece: First-Use Journey Documentation

### The Architectural Problem

Salesforce deployment carries a specific psychological weight that Gearset's
existing documentation did not address. Users arrive with trepidation, not
because the product is difficult, but because the consequences of a 
deployment error in production are severe enough to make even experienced
admins hesitate.

Documentation that leads with mechanics rather than orientation meets an 
anxious user with complexity. The result is a self-fulfilling prophecy:
the user's nervousness increases their likelihood of mistakes, and the
possibility of mistakes causes them to postpone the deployment entirely.
Both outcomes cost the company. The nervous user who deploys incorrectly
generates a support ticket. The user who postponed generates a stalled 
onboarding and an increased churn probability.

Gearset's existing documentation was organized around what the user does.
It wwas not organized around what the user feels when they arrive at it.

### The Pattern Chosen

This guide uses the journey pattern, organized around the user's psychological
progression from trepidation to confident execution rather than around Gearset's
feature sequence.

Each stage is named for its outcome, not its feature. Each stage closes with
an explicit checkpoint that confirms progress before the next stage begins. 
Potential failure modes are documented inline at the point where they are
most likely to occur, not collected in a troubleshooting FAQ the anxious
user will never reach. The rollback constant is disclosed in the prerequisite
section, before the first step, so the user makes their plan decision with
full information rather than discovering the limitation after they need it.

The steps are designed to be repeatable. A user who completes this guide once
has a process they can execute confidently on every subsequent deployment without 
returning to the documentation.

### The Commercial Consequence Prevented

A user who completes their first Gearset deployment confident does not need a
support ticket. A user who understands the failure modes before encountering
them resolves most issues independently. A user whose process is repeatable
from the first deployment does not search for third-party how-to blogs or
YouTube tutorials to fill gaps the official documentation left open.

This guide is designed to make Gearset's support team less busy, not more.
Every inline warning, every stage checkpoint, every if-then failure path
exists to answer the question before the user thinks to ask it.

The measure of this document's success is not whether users find it clear. It
is whether users who read it deploy successfully on their first attempt and never
need to return to it for guidance on a process they now own.

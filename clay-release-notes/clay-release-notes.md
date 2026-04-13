# Credit System Update — Release Notes
**Version:** Clay Platform Update 2.0  
**Effective Date:** March 11, 2026  
**Affected Plans:** Starter, Growth, Enterprise

## Summary
Clay's credit system now separates platform usage from data 
purchasing into two distinct currencies: 
Actions and Data Credits. Existing workflows built against 
the previous single-credit model will consume 
credits differently under the new system and should be reviewed 
before your next billing cycle.

## What Changed

### Actions
Actions measure platform usage: enriching data, running AI research 
and sending data to external tools.
Each enrichment or execution task consumes 1 Action regardless of the 
data source or provider used.

Actions are included in your Clay plan as a background meter.
90% of users will not reach their Actions limit under normal usage.

**What this means for you:** Actions replace the orchestration
component of the previous credit system. If you were previously tracking
credit consumption primarily against enrichment volume, Actions now cover 
that layer.

### Data Credits
Data Credits are used to purchase data from Clay's marketplace and AI 
from third-party providers.
Unlike Actions, Data Credit consumption varies by data type and provider.

Typical cost per fully enriched record: 6 to 20 Data Credits depending on the
data types enriched. Emails cost fewer credits. Phone numbers cost more.

**What this means for you:** Data Credits replace the data purchasing component
of the previous credit system. Users who connect their own API keys for existing 
data
provider subscriptions eliminate the Data Credit cost for those providers while 
still consuming 1 Action per enrichment.

### The Separation
Previously, a single credit covered both platform usage and data purchasing.
The new system separates these into two distinct meters to give visibility into
what you are paying for at each layer.

## Who is Affected
**All paid users** are affected by this change. The credit system update applies
to Starter, Growth, and Enterprise plans.

The degree of impact depends on your current workflow:

**High impact:** Users who built workflows under the previous single-credit model
without connecting their own API keys. Your credit consumption patterns will change
under the new system. Review your workflow before your next billing cycle.

**Medium impact:** Users who connect some external API keys but rely on Clay's marketplace
for others. Your consumption will change for the marketplace-sourced data. Review those
specific enrichment columns.

**Low impact:** Users who connect their own API keys for all data providers.
Your Data Credit consumption will be minimal. You will primarily consume Actions,
which are included in your plan.

**No impact:** Free plan users. Your 100 monthly credits continue under the 
existing free plan structure.

## What To Do

### Before Your Next Billing Cycle

**Step 1: Check your current credit balance.**
Go to Settings → Credit Usage. Review your current Actions balance and Data
Credits balance separately. Note your consumption pattern from the last 30 days.

**Step 2: Identify your high-consumption enrichment columns.**
In your most-used workbooks, identify which enrichment columns consume the most credits.
Phone number enrichments and AI research columns will show the highest Data Credit
consumption under the new system.

**Step 3: Connect your existing API keys if you haven't already.**
If you subscribe to data providers outside Clay, connecting your API keys eliminates
the Data Credit cost for those providers. Go to Settings → Integrations to connect
existing subscriptions.
**Tip:** Connecting external API keys can reduce Data Credit consumption by 50 to 80
percent for those providers.

**Step 4: Adjust your plan if needed.**
If your review shows that your current plan's Data Credit allocation does not cover
your typical monthly usage under the new model, adjust your plan before your next billing
cycle to avoid running short mid-cycle.
Go to Settings → Plans & Billing → Switch Plan

### If You Are Mid-Cycle Right Now

If your billing cycle is within the next 7 days, prioritize Step 1 and Step 2 immediately.
You may not have to adjust your plan before renewal. Monitor your balance daily until 
the cycle resets.

> **Warning:** Auto-Update triggers enrichments automatically when
> input values change. If Auto-Update is enabled on high-consumption columns, disable
> it temporarily while you assess your consumption pattern under the new system.
> Go to the enrichment column settings and toggle Auto-Update off.

## Migrating Existing Workflows

If you built workflows under the previous credit system, use this guide to assess 
and adjust them.

### Understanding Your New Consumption Pattern

Under the previous system, each enrichment consumed a single credit covering both
platform usage and data cost.

Under the new system, the same enrichment consumes:
- 1 Action (platform usage, fixed)
- Variable Data Crdits (data cost, depending on provider and data type)

**To estimate your new monthly consumption:**

1. Go to Settings → Credit Usage → Table History
2. Select your highest-volume workbook
3. Review the breakdown of Actions versus Data Credits for the last 30 days
4. Multiply by your typical monthly volume to project forward

### Optimizing Your Workflows Under the New Model

**Filter before enriching.**
Enriching records that don't match your ICP wastes both Actions and Data Credits.
Add a disqualification column before your enrichment columns to exclude non-ICP records
from running.

**Use waterfall enrichment strategically.**
If a provider fails to return data, you are not charged Data Credits for that failed
lookup. Structure your waterfalls to try cheaper providers first and more expensive
ones only when cheaper providers fail.

**Set credit spend limits on high-volume workbooks.**
Enterprise plan users can set workbook-level credit spend limits to prevent any single
workbook from consuming more than its allocated share. Go to Workbook Settings →
Credit Spend Limit → Manage.

## Resources
- [Full Credits Documentation](https://university.clay.com/docs/credits) — Complete
  guide to Actions and Data Credits including AI pricing, rollover rules, and workbook limits.

- [Plans & Billing](https://university.clay.com/settings/credit-usage) —
  Direct link to your workspace credit consumption data.

- [Credit Usage Dashboard](https://app.clay.com/settings/credit-usage) — Direct
  link to your workspace credit consumption data.

- [Clay Community Slack](#) — Post in #pricing-questions for peer support from Clay power
users and the Clay team.

---
*These release notes cover the Clay Platform effective March 11, 2026. For changes
prior to this date, see the [changelog archive](#).*

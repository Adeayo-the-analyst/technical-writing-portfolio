# Your First Deployment with Gearset

Gearset replaces the manual, error-prone process of Salesforce metadata deployment with
a comparison-driven workflow that shows exactly what will change before anything
moves.

This guide takes you from connecting your Salesforce orgs to completing your first
successful deployment to production. It covers the full journey: comparison, dependency
analysis, validation, deployment, and what to do if something needs to be reversed.

By the end of this guide you will have deployed metadata changes between two Salesforce
environments using Gearset's compare and deploy workflow.

## Before You Begin
**You will need:**
- A Gearset account (free trial or paid plan)
- Administrator access to at least two Salesforce orgs (source and target)
- Your Salesforce login credentials for both orgs

**Plan tier note:**
Gearset's rollback feature, which reverses a deployment if something goes wrong after
release, is available on the Teams plan and above. If you are on the Essentials plan and
need to reverse a production deployment, you will need to deploy the previous metadata
manually or upgrade your plan.

If production deployment risk is a primary concern for your team, review Gearset's plan
options before your first production deployment.

## What You Will Accomplish

This guide covers one complete deployment workflow:

1. Connect your source and target Salesforce orgs to Gearset
2. Run a metadata comparison between your environments
3. Select the metadata changes you want to deploy
4. Review Gearset's dependency analysis and problem detection
5. Validate the deployment against your target org
6. Execute the deployment and review the results

Each stage builds on the previous one. Complete them in order for your first
deployment.

## Stage 1: Connect Your Salesforce Orgs

Before running a comparison, Gearset needs access to your Salesforce environments.

### Connect Your Source Org

Your source org is the environment where your changes live. This is typically a 
sandbox or developer org where you built or tested the metadata you want to deploy.

1. In Gearset, navigate to **Connections** in the left sidebar.
2. Click **Authorize a new org**.
3. Select **Salesforce** as the org type.
4. Enter a recognizable name for this org
   (for example: "Dev Sandbox — April 2026").
5. Click **Authorize** and complete the Salesforce login prompt that appears.
6. Confirm the org appears in your Connections list with a green status indicator.

### Connect Your Target Org

Your target org is the environment you are deploying changes into. For this guide,
this target is your production org or a staging environment that mirrors production.

Repeat the steps above for your target org, using your production or staging credentials.

> **Note:** Gearset connects to your orgs using OAuth authentication. Your
> Salesforce password is never stored by Gearset. The connection uses a secure
> token that you can revoke from your Salesforce org settings at any time.

---
**✓ Stage 1 complete.**
Both your source and target orgs appear in your Connections list with green status
indicators. You are ready to run your first comparison.

---

## Stage 2: Run Your First Comparison

A comparison shows you exactly what metadata differs between your source and target orgs.
You choose what to deploy from the comparison results. Nothing moves until you explicitly
select and deploy it.

### Select Your Source and Target

1. From the Gearset dashboard, click **Compare & Deploy**.
2. Select your source org from the left dropdown.
3. Select your target org from the right dropdown.
4. Click **Compare Now**.

### Read the Comparison Results

The comparison results are organized in three tabs:

- **New:** Metadata that exists in your source but not in your target. Deploying
these items will create them in your target org.
- **Changed:** Metadata that exists in both orgs but differs between time. Deploying these
items will overwrite the target version with the source version.
- **Deleted:** Metadata that exists in your target but not in your source. Deploying
these items will remove them from your target org.

 > **Warning:** Items in the Deleted tab will be permanently removed from your
> target org when deployed. Review these items carefully before including them
> in your deployment.

### Understand the Diff Viewer

Clicking any metadata item in the comparison results opens the diff viewer below
the table. The diff viewer shows the specific differences between the source and target
versions of that item at the XML level.

You do not need to read XML to use Gearset. The diff viewer is available for users who
want line-level visibility into exactly what will change. For most deployments, reviewing
the item name and change type in the comparison table is sufficient.

---
**✓ Stage 2 complete.** You can see the metadata differences between your source 
and target orgs organized by change type. You are ready 
to select what to deploy
Gearset will retrieve the metadata from both orgs and display the differences. Depending
on your org size, this may take 30 seconds to several minutes.

---

## Stage 3: Prepare Your Deployment

### Select Metadata Items

From the comparison results, select the items you want to include in your deployment
by clicking the checkbox next to each item's name.

**To select all items in a tab:** Click the checkbox in the header row of the table.

**To view your current selection:** Click the **Selected Items** tab at any point
to review everything you have chosen before proceeding.

### Identify and Include Dependencies

Gearset automatically detects dependencies between metadata items. A dependency
means that one item requires another item to be present in the target org to function
correctly.

To view an item's dependencies, click the arrow next to its name to expand the 
dependency tree. Gearset organizes dependencies into four categories:

- **Components:** The constituent parts of the parent item
- **Depends on:** Items your selection requires in the target org to deploy
  successfully
- **Profiles and permissions:** Related access control changes associated with your selection
- **Used by:** Items in the target org that depend on your selection

> **Warning:** If your selection has items listed under **Depends on** and those
> items have changed in your source, include them in your deployment. Deploying
> without required dependencies is the most common cause of deployment failure.

### Review Gearset's Problem Analysis

After selecting your items, click **Next**. Gearset will automatically check your
selection for missing dependencies and potential deployment problems.

If Gearset identifies issues, it will suggest specific fixes. For each suggestion:
- **Accept the suggestion:** Tick the checkbox and click **Pre-deployment summary**.
  Gearset adds the missing item to your selection.
- **Review and adjust:** Click **Back to comparison** to modify your selection manually.
- **Proceed without fixing:** Leave the checkbox unticked and click **Pre-deployment summary**.
  Your deployment may fail if the issue is not resolved.

> **Tip:** Accept Gearset's suggestions on your first deployment unless you have
> a specific reason not to. The problem analyzer has context about your org's
> dependency structure that is difficult to replicate through manual review.

---
**✓ Stage 3 complete.** Your metadata selection is finalized and Gearset's problem
analysis has been reviewed. You are ready to validate your deployment.

---

## Stage 4: Validate Your Deployment

Before deploying to production, validate your deployment against the target org.
Validation runs Salesforce's deployment checks without making any changes, confirming your
package will deploy successfuly.

1. On the pre-deployment summary page, click **Validate deployment**.
2. Gearset will run Salesforce validations and, if your selection includes Apex classes,
   the relevant Apex tests.
3. Review the validation results before proceeding.

**If validation passes:** Your deployment is ready.
Proceed to Stage 5.

**If validation fails:** Review the error messages in the validation results. Common
causes include:

- Missing dependencies not caught by problem analysis
- Apex test failures caused by changes in your selection
- Profile or permission conflicts between source and target

Resolve the identified issues, return to Stage 3 to adjust your selection, and revalidate.

>**Note:** Validation against a production org counts against your
>Salesforce API limits. For large orgs with high API usage, schedule validations during
>off-peak hours.

--- 
**✓ Stage 4 complete**. Your deployment has passed validation. No changes have been made
to your target org yet. You are ready to deploy.

---

## Stage 5: Deploy to Production

You have compared your environments, selected your metadata, reviewed dependencies, and 
validated your package. You are ready to deploy.

1. Click **Deploy now** on the pre-deployment summary page.
2. Gearset will upload your package to Salesforce and queue it for release.
3. Monitor the deployment progress on the deployment status page.

>**Note:** You can safely navigate away from the deployment status page. The deployment
>will continue running in the background. Return to **Deployment history** at any time
>to check its status.

### Read the Deployment Summary

When the deployment completes, Gearset displays a deployment summary showing:

- Total components deployed
- Components that succeeded
- Components that failed, if any
- Apex test results, if applicabe

**If all components succeeded:** Your deployment is complete. The metadata changes
from your source org are now live in your target org.

**If any components failed:** Review the error details in the deployment summary. 
Failed components were not applied to your target org. The components that succeeded
were applied and remain in place.

---
**✓ Stage 5 complete**. Your first Gearset deployment is complete. Your source
metadata changes are now live in your target org.

---

## If Something Goes Wrong

### What Gearset Resolves Automatically

Gearset's problem analyzer catches the most common deployment issues before they reach
production. If you followed the problem analysis recommendations in Stage 3, most preventable
failures will have been addressed before deployment.

For deployment failures that occur despite validation, the deployment summary error details
are your first diagnostic resource. Each failed component includes an error message that identifies
the specific issue.

### Rollback: Reversing a Completed Deployment

If a completed deployment causes unexpected behavior in your target org and you need to
reverse it, Gearset's rollback feature restores the previous metadata state for the deployed
components.

**Rollback is available on Teams plan and above.**

If you are on the Essentials plan, rollback through Gearset is not available. To reverse a
deployment on the Essentials plan:

1. Identify the metadata components that need to be reversed using Gearset's deployment
   history.
2. Use Gearset to compare your target org against a backup or your previous source state.
3. Deploy the previous versions of the affected components back to your target org manually.

If production rollback capability is a requirement for your team's release process, upgrade to
the Teams plan before deploying to production.

### When to Contact Gearset Support

Contact Gearset support if:

- Your deployment fails with an error message that does not match the common causes listed above
- Gearset's problem analyzer and your manual review did not identify the issue before deployment
- You need guidance on a complex dependency scenario specific to your org's configuration

Gearset support is available from live chat from within the product. Every Gearset subscription 
includes access to support from the Gearset team directly.

## Next Steps

You have completed your first Gearset deployment.

Based on how you plan to use Gearset, your next steps will differ:

**If you are a solo admin managing a single org:** 
Explore Gearset's backup and monitoring features to protect your org's metadata and
track changes over time.
→ [Set up automated backups](#)
→ [Configure org monitoring](#)

**If you are working with a development team:** Connect Gearset to your version control
repository to bring your deployment workflow into a Git-based pipeline.
→ [Connect a Git repository](#)
→[Run your first CI/CD pipeline](#)

**If you are managing multiple orgs or client environments:** Explore Gearset's pipeline
features to manage deployments across multiple environments with approval workflows and
automated testing
→ [Set up a deployment pipeline](#)
→[Configure automated testing](#)



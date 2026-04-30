# Git Workflows 101
This is designed to understand GitHub Flow while understanding alternative Git workflows.

Focus areas on: team governance, branch protection, and explicit merging - maintaining a clear audit trail.

## 1. Overview of Git Workflows 
Understanding these 3 -three primary workflows used in the industry:
* __GitHub Flow__: Ideal for agile teams and web applications. It relies on a single `main` branch that must always be in a deployable state. Feature branches are used for all changes.
* **Git Flow**: A more structured approach with multiple long-lived branches (`main`, `dev`, `release`, `feature`, and `bug`). It is ideal for installable applications (like mobile apps) where multiple versions run simultaneously.
* **Trunk-Based Development**: The current industry standard (2026) for  large-scale SaaS. It uses direct commits to `main` or very short-lived feature branches (~4 hours) and relies on "feature flags" and bulletproof automated testing.

## 2. Branch Protection and Repository Setup
Case Scenario - 5 Group members working on a project

__Member 1__ will act as the "team lead" for this lab.

1. __Confirm that your Team Members are Collaborators__: Go to __Settings__ > **Collaborators**. One should see all the members listed with "Write" access or "Admin" access

2. __Configure Branch Protection__
* Go to **Setting** > **Branches** **Add Branches ruleset**
* Create a rule named `pr-and-1-approval-required-to merge.`
* Set the enforcement status to **Active**
* Include the default branch as the target
* **Enable**: "Require a pull request before merging" and set "Required approvals" to 1
* This ensures that no team member can bypass the review process. At least 1 other team member must agree with the changes before they can be merged into main.
* Go to **Settings** > **Rulesets** and confirm that the new ruleset is active and correctly configured.

3. __Create a Project__
1. Go to the **Projects** tab in the repository and click on **New Project**
2. Select the **Iterative Development** template and name it "**[Project Name]...**
3. Ensure that your team members are added to the project as collaborators with **Admin** rights. This can be done in the project **Settings** > **Manage Access**
4. Create iterations and specify the start and end dates for each iteration. This is available under **Settings** > **Iterations** 

4. __Create Milestones__
1. Go to the issues tab and click on **Milestones**.
2. Create 3 milestones and:
    * Assign appropriate due dates for each to align with the iterations you set up in the project.
    * Add an appropriate description for each milestone to clarify the goals and expectations
        * 50% Complete Milestone
        * 75% Complete Milestone
        * 100% Complete Milestone

5. __Creating the Task Backlog (All Members)__
Determine the specific technical tasks that need to be completed.
Define each task clearly and assign to a specific team member.
Once tasks have been identified, follow these steps:

    1. Each member must create a "GitHub Issue" to represent a specific technical task.
    2. Each issue should be assigned to the respective member of the team.
    3. Each issue should be assigned the label "**enhancement**".
    4. Each issue should be assigned the type "**Feature**"
    5. Each issue should be assigned to the "[Project Name]... project"

Example issues:
    * **Member 1**: Issue #1 - 50% Complete Milestone - Title: feature/project-name/update-project-README. Description: Update the project's README with team roles.
    * **Member 2**: Issue #2 - 50% Complete Milestone - Title: feature/project-name/research-on-data-sources. Description: Create a data_source.md file reviewing sources of data in a business.
    * **Member 3**: Issue #3 - 50% Complete Milestone - Title: feature/project-name/research-on-star-schema. Description: Create a warehouse_schema.md describing a Star Schema.
    * **Member 4**: Issue #4 - 75% Complete Milestone - Title: feature/project-name/research-on-ETL-ELT-EtLT. Description: Create a data_pipeline.md differentiating between ETL, ELT, and EtLT in the context of compliance with the legal requirements in an industry.
    * **Member 5**: Issue #5 - 100% Complete Milestone - Title: feature/project-name/research-on-data-governance. Description: Add a governance.md file reviewing data governance and access to PII.

6. __Assigning Issues to Iterations and Managing the Status of Issues__ 
1. Go to the Projects tab and open the "__[Project Name]__" project. Navigate to the **My items** view where you can see all the issues in the backlog.
2. For each issue, click on the issue title and assign it to the appropriate iteration based on its milestone. Example:
    * Issues #1, #2, and #3 are planned for Iteration 1, which corresponds to the **50% Complete Milestone**.
    * Issue #4 is planned for Iteration 2, which corresponds to the **75% Complete Milestone**.
    * Issue #5 is planned for Iteration 3, which corresponds to the **100% Complete Milestone**.

One should see the issue under the "**current iteration**" tab of the project listed in the Backlog.

Issues can move across 5 states by default: *Backlog*, *Ready*, *In Progress*, *In Review*, and *Done*.
* **Backlog**: The issue is created but not yet started.
* **Ready**: The issue is ready to be worked on but has not been started yet.
* **In Progress**: The issue is currently being worked on.
* **In Review**: The issue has been worked on and is being reviewed by others, i.e there is a code review before the Pull Request is approved and merged.
* **Done**: The issue has been completed, approved, and merged into the main branch through the Pull Request process.

The team members should have daily brief meetings to discuss the status of their assigned issues and update the status accordingly in the project board. This helps in tracking the progress of each task and ensures that everyone is on the same page regarding the project's timeline and deliverables.

Such meetings are similar to "stand-up meetings" in agile development, where team members quickly share updates on their work, any blockers they are facing, and their plans for the day. This promotes transparency and collaboration within the team. It helps you to avoid surprises a few hours to the deadline.

7. __The GitHub Flow Cycle__

Each member must follow these steps for their respective issue.

**Member 1** will follow these steps last
**Step A: Branching**
On your local machine, create and switch to a new branch for your task.
Note: The branch name should follow the format `feature/project-name/description` to maintain clarity and consistency across the team. 
For example, if you are working on an Issue then your branch name could be feature/project-name/data-source. This naming convention helps everyone in the team quickly understand the purpose of the branch and its connection to the corresponding lab.
```bash
git checkout -b feature/project-name/description
```
*Note: A branch is an independent line of development used for team governance.*

**Step B: Working and Committing**
Create your assigned file and confirm that there is a modification ready to be committed.
```shell
git status
```
You can configure the default commit message editor to be **VS Code** for better formatting of the commit message body. Run the following command:
```shell
git config --global core.editor "code --wait"
```

Once ready, stage and commit it:
git add .
git commit

**Important**: What constitutes an **academically sound** commit message?
A commit message is a permanent, public record of **why** a change was made — not merely what changed (the diff already shows that). In an academic context, it serves the same function as a lab notebook entry: it must be comprehensible to a reader who has no prior context and who may be reviewing the work weeks later.

Your `git commit` command (without the `-m` flag) will open a text editor. Structure your message as follows:

```shell
<Verb in imperative mood> <concise description of the change> (≤72 characters)

<Blank line — mandatory>

Why this change was made:
<One to three sentences explaining the academic or technical motivation.
What problem does this address?
What would happen without this change?>

Related issue: #<issue-number>
```

Why the **imperative mood?** Git itself uses it — "Merge branch", "Revert commit", "Add file". Reading your message alongside Git's own messages should feel consistent. Write "Add feature" rather than "*Added feature*" or "*Adding feature*".

Example:
```bash 
Add data_source.md listing primary project name source types

This file documents the four primary data source categories used
in Business Intelligence architectures: transactional databases,
flat files, APIs, and streaming sources from various departments.

It is important to understand these categories as they inform the
design of data pipelines and the choice of tools for extraction
and transformation.

Related issue: #2
```

__Step C: Pushing and Pull Request__

Push your brach to GitHub

```shell
git push origin feature/lab-number/description
```
1. Go to GitHub (the website) and open a **Pull Request (PR)** from your branch to main. There should be a green button prompting you to "Compare & pull request" after pushing. If not, then you can navigate to the "**Pull requests**" tab and click on "New pull request" to select your branch and create the PR.

2. Name the PR appropriately, e.g., "`Merge feature/project-name/update-project-readme into main`" and add a detailed description of the changes made. This description should provide context for the reviewer, explaining the motivation behind the changes and any relevant details that would help them understand the purpose of the PR.

3. Link the PR to the corresponding issue by including `#issue-number` in the PR description. This creates a connection between the changes and the issue it addresses. A common way to include the issue number is to use the text "Closes `#issue-number"` in the PR description, e.g., `"Closes #2"`. This not only links the PR to the issue but also automatically closes the issue when the PR is merged.

4. Assign a teammate to perform a **Code Review**. If this was your research/project, then your research supervisor would be the assigned reviewer. The author of the PR should not merge their own PR. This is a critical aspect of team governance and ensures that all changes are reviewed by at least one other team member before being integrated into the main branch.

5. The assignees can be anyone who contributed to the commits in the branch, the label can be "**enhancement**" for a new feature, the projects should be the 202604 Business Intelligence Labs, and the milestone should correspond to the one assigned to the issue that the feature branch addresses.

__Step D: The Code Review__

* **The Reviewer**: Check the Files changed for clarity and accuracy based on the source material. Approve the PR if it meets requirements. If not, request changes and provide specific feedback in the comments.
* **The Author**: Address any feedback provided during the review. If it is approved, then the author can proceed to merge the PR. If changes are requested, make the necessary updates and push them to the same branch. The PR will automatically update with the new commits, and the reviewer can re-review until it is approved.

**Step E: Merging WITHOUT Fast-Forward (--no-ff)**
Once approved, the merge must be performed. To ensure the process is visible for audit purposes, we will avoid "Fast-Forward" merging. Click the green "Merge pull request" on the GitHub web interface, then select "Create a merge commit" to ensure that the merge is explicitly recorded in the history. This should achieve the same result as running the following command in the terminal:

```bash
git merge --no-ff feature/project-name/description
```
After successfully merging the pull request in the web browser, team members should pull the latest changes to their local main branch to stay up to date:

```shell
git checkout main
git pull origin main
```

**Why** **--no-ff** ? This option always creates a "merge commit," documenting the integration as a deliberate event in history. This is ideal in academic contexts so that research supervisors can see the branch evolution and your collaborative process. It also enables the lecturer to see the history of changes in a more structured way, which is beneficial for grading and feedback.

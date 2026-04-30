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



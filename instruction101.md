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







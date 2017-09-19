
# EDS Identity Management Git Standards
##### These repository guidelines should be followed when working on any EDS Identity Management application.
##### For any questions regarding these, please reach out to your tech lead.

## Master 
  **Name:** master
    
  **Purpose:** Represents the current state of PROD
  
  **Usage:**
  + This will *not* be developed against directly, except for emergency release fixes (via **Feature** or **Hotfix** branches) on PROD night or an off-schedule release
  + This will *never* be deleted

  **Tags:**
  + Tags represent the release merge into Master
  + *convention:* **vM.R.YY**
  + *example:* 
    1. **v9.0.17** for the standard September Application release in 2017
    2. **v9.1.17** for the first September 2017 off-schedule release
    3. **v10.2.17** for the second October 2017 off-schedule release

## Develop
  **Name:** develop
    
  **Purpose:** Represents merged, stable "release candidate" code (similar to SVN trunk)
  
  **Usage:**
  + This will *never* be developed against directly
  + This will *never* be deleted

## Project Branches
  **Name:** 
  + *convention:* **project/[short-description]**
  + *example:* 
    1. **project/preferences-phase-2**
    2. **project/postal-mail-reduction**
  
  **Purpose:** Represents all development for a single project

  **Usage:**
  + These will be created from **[develop](#develop)** prior to working on story/tech/defect cards for non-emergency-release effort
  + These will be developed against (via **[feature](#feature-branches)** branches) during the standard DDIT cycle.
  + These will be deleted on a case-by-cases basis, sometime after release.

## Release Branches
  **Name:** 
  + *convention:* **release/[year]/[number]**
  + *example:* 
    1. **release/2017/9.0**
    2. **release/2017/10.2**
  
  **Purpose:** Represents release-ready code (which could be multiple projects that have all been merged into **[develop](#develop)**)

  **Usage:**
  + These will be created from **[develop](#develop)** prior to pushing code to ST and developed against (via Feature branches) during the System Test cycle.
  + These will be merged to **[master](#master)** after a PROD release.
  + These will be merged to **[develop](#develop)** with each change (ie: a System Test defect fix).
  + These will be deleted on a case-by-cases basis, sometime after release.

## Feature Branches
  **Name:** 
  + *convention:* 
    1. **feature/rtc/[RTC number]**
    2. **defect/qc/[QC number]**
  + *example:* 
    1. **feature/rtc/951023**
    2. **defect/qc/513772**
  
  **Purpose:** Represents development of a single story, tech, or defect card.

  **Usage:**
  + Project/Release
    + These will be created from a **[project](#project)** or **[release](#release)** branch each time a developer picks up a new unit of story/tech/defect work.
	+ These will be merged to the **[project](#project-branches)** or **[release](#release-branches)** branch before being deployed.
	+ These will be deleted after sign-off.
  + Master
	+ These will be created from **[master](#master)** each time a developer works on an emergency release fix.
	+ These will be merged to **[master](#master)** and **[develop](#develop)** before being deployed.
	+ These will be deleted after being verified post-deployment.

## Hotfix Branches
  **Name:** 
  + *convention:* **hotfix/[short-description]**
  + *example:* **hotfix/claims-link-change**
  
  **Purpose:** Represents development of non-story/tech/defect card work (a small refactor or a quick fix)

  **Usage:**
  + Project/Release
    + These will be created from a **[project](#project)** or **[release](#release)** branch each time a developer picks up a new unit of story/tech/defect work.
	+ These will be merged to the **[project](#project-branches)** or **[release](#release-branches)** branch before being deployed.
	+ These will be deleted after being verified post-deployment.
  + Master
	+ These will be created from **[master](#master)** each time a developer works on an emergency release fix.
	+ These will be merged to **[master](#master)** and **[develop](#develop)** before being deployed.
	+ These will be deleted after being verified post-deployment.

## Externalized Property Files
  **Purpose:** Repositories separate from application code to handle data sensitive to the application, such as passwords
  
  **Name:**
  + *convention:* **Nationwide/[application]-resources**
  + *example:* **Nationwide/cam-resources**
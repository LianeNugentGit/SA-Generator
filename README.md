Service Appointment Generator Package
Some jobs require a group of resources with varied skills, to go on-site over the course of multiple days. Some skills are not required for the whole duration. Some skills are not required for the whole day of work. Job planners need the ability to build these dynamic crews for multi-day jobs and see the availability and skills of the resources on a single screen:

Wanting in day changes to the Crew Member/Job Assignment i.e. a crew member called in sick on Monday and we need to send someone in just for that day
Partial job assignment to a new Crew Member for a single day of the multi-day i.e. tech assigned on Monday but will see the whole week on the mobile app and also doesn’t get alerted or have an Assigned Resource created
When various skills are required throughout the duration of the job i.e. need someone with troubleshooting skills for the first day, then a mechanic the second day, then an electrician the third day (team approach)
Solution
This package will allow a user to create and assign multiple service appointments for a single work order on a single screen. This will provide a stop-gap accelerator-style solution that will be an unmanaged package, with access to the source code, for customers to modify.

It does not use the scheduling features of Salesforce Field Service but the scheduler user can use the SFS Gantt to review and manage violations and perform scheduling actions like drag and drop, candidates, RSO, etc on these service appointments.
Crews are not used/supported in this package
Multi-day work is not used/supported in this package
Multi-day absences are not used/supported in this package
There is a dependency on the UnofficialSF Package for Datatable. Safe Harbor: Standard Datatable Flows will eventually be added to the platform and is currently in Pilot.
Basic Installation Notes
Install Base and Screen Base packs (https://unofficialsf.com/flow-action-and-screen-component-basepacks/)
Install Datatable (https://unofficialsf.com/datatable-lightning-web-component-for-flow-screens-2/)
Install the Service Appointment Generator package
Sandbox Installation Link: https://test.salesforce.com/packaging/installPackage.apexp?p0=04t8c000000a89S
GitHub Repository: https://github.com/cxalbanese/multiresource.git
Deactivate the Validation Rule on Service Appointment [Dont_allow_scheduled_or_dispatched].
Assign the permission set called [MR_DT_Permission_Set] to the admin users and the scheduling users who will use this package.
Add the flow called [Multi Resource Assignment Wizard] to your work order lightning page and make sure to pass the record ID into this variable is checked on the flow component.
Optionally use the Header and Collapsible Right Sidebar template [MR_DT_Template] for the work order page.
Additional installation details can be found in the documentation here: https://salesforce.quip.com/xsgaA6pCTP1t#temp:C:LHS21bff2fd7b32415ba9110dcd4

V1.2 Changes - June 18, 2024
Cleaned up the package from attributes that could cause that package to fail and removed files that are not required.
V1.1 Changes - Jan 24, 2024
Cleaned up the package from attributes that could cause that package to fail.
V1 Changes - Dec 13, 2022
As a Scheduler, I want to define the Skills and Skill Levels required at the Work Order and when selecting Service Resources I would like to see how closely their skills match to the skills required on the Work Order.
As a Scheduler, I'd like to see what skills are missing in the selection screens so that I can be aware, right away that I'll have a staffing issue.
As a Scheduler, I want to know if there are any existing conflicts for a set of Resources for a given date range which will help me select the Resources that are most available and will help me select the Dates that do not have any conflicts.
As a Scheduler, I'd like an option to build a schedule for only weekends.
Added Features:
Technician Missing Skill Checker and Skill Matcher - This displays skills that the technician has, including those matching on skill level and those not. it also displays a summary of the skill match counts for each technician.
Work Order Missing Skill Checker - This displays a summary of the skills that are missing from the available technicians when compared to the work order required skills. It also displays a summary of the skills that are missing from the selected technicians when reviewing the generated service appointments.
Overlap / Availability Checker - This displays a summary of any overlaps that are encountered. It displays Resource Absences and Service Appointments that already exist for the pool of technicians and the selected technicians. It also provides a summary of availability.
New Fields - new fields have been added to Service Territory Member and Service Appointment to hold the overlap information.
SkillRequirement.MR_DT_Skill_Name_and_Level__c - formula field to display skill name and level - used to display required skills on WO
ServiceAppointment.MR_DT_Conflict_Details__c - text field to display the list of RAs/SAs in conflict with current SA date
ServiceAppointment.MR_DT_Percent_Availability__c - text field displaying % of availability for the tech for the current SA date
ServiceAppointment.MR_DT_Skill_Levels_Matched__c - text field displays the ratio of skill levels matched to required, for example, 3/5
ServiceAppointment.MR_DT_Skill_Names_Matched__c - text field displaying the list of skills matched regardless of whether levels match
ServiceAppointment.MR_DT_Skills_Matched__c - text field displaying the list of skills and skill levels matched
ServiceTerritoryMember.MR_DT_Skill_Levels_Matched__c - text field displays the ratio of skill levels matched to required, for example, 3/5
ServiceTerritoryMember.MR_DT_Skill_Names_Matched__c - text field displaying the list of skills matched regardless of whether levels match
ServiceTerritoryMember.MR_DT_Skills_Matched__c - text field displaying the list of skills and skill levels matched
ServiceTerritoryMember.MR_DT_Percent_Availability__c - text field displaying % of availability for the tech for the current SA date
Lightning Page Template with expandable main section - this Work Order Lightning Page template provides more room for the user. You will have to modify and set this page to be your new Work Order Lightning Page for users.
New Classes
MRDTGetOverlapInfo - calculates whether there are existing RAs and/or SAs that overlap with the new SAs being generated
MRDTSkillMatcher - calculates skill matching profile for each service resource displayed. also calculates the skills that are not present on the service resources displayed.
MRDTresourceOverlaps - this is the resource overlap and skill profile. This class performs no processing, it's simply the data structure
Miscellaneous Notes
In the flow [MR DT Service_Appointment_Creator], the screen called [Select_Resource] has the display of a field called [outputOverlapDebug]. This is intended to help you inspect the results from the overlap checking.
Remove this field or use component visibility to hide it from the user

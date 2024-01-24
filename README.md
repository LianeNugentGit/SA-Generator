#Service Appointment Generator Package
Some jobs require a group of resources with varied skills, to go on-site over the course of multiple days. Some skills are not required for the whole duration. Some skills are not required for the whole day of work. Job planners need the ability to build these dynamic crews for multi-day jobs and see the availability and skills of the resources on a single screen:

Wanting in day changes to the Crew Member/Job Assignment i.e. a crew member called in sick on Monday and we need to send someone in just for that day
Partial job assignment to a new Crew Member for a single day of the multi-day i.e. tech assigned on Monday but will see the whole week on the mobile app and also doesn’t get alerted or have an Assigned Resource created
When various skills are required throughout the duration of the job i.e. need someone with troubleshooting skills for the first day, then a mechanic the second day, then an electrician the third day (team approach)

#Solution
This package will allow a user to create and assign multiple service appointments for a single work order on a single screen. This will provide a stop-gap accelerator-style solution that will be an unmanaged package, with access to the source code, for customers to modify.

It does not use the scheduling features of Salesforce Field Service but the scheduler user can use the SFS Gantt to review and manage violations and perform scheduling actions like drag and drop, candidates, RSO, etc on these service appointments.
Crews are not used/supported in this package
Multi-day work is not used/supported in this package
Multi-day absences are not used/supported in this package
There is a dependency on the UnofficialSF Package for Datatable. Safe Harbor: Standard Datatable Flows will eventually be added to the platform and is currently in Pilot.


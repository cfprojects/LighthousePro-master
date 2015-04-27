ReadMe

LICENSE 
Copyright 2010-2014 Raymond Camden

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
   
  

This application was created by Raymond Camden (raymondcamden@gmail.com). 
If you find this application worthy, I have a Amazon wish list set up (www.amazon.com/o/registry/2TCL1D08EZEYE ). 
Gifts are always welcome. ;)

Last Updated: 5/23/2014 (2.9.3)
Fix by Alan Holden to allow for a specified attachment path.

Last Updated: 9/1/2012 (2.9.2)
/config/ColdSpring.xml.cfm - version
/views/milestones.cfm - added a random url to help fix an Ajax caching issue
/install/mysql.sql - typo

Last Updated: 11/29/2011 (2.9.1)
/config/ColdSpring.xml.cfm - version
Credit Sebastiaan van Dijk for noticing Project Deletion did not clean up attachments or announcements!

Also noticed in user deletion I didn't remove their filters.

Minor UI fix with errors.

Many files updated - I think it would be easier to consult the SVN history to get a list. On top of the above, I've added "archived"
as a property to issues (and filters - so please add a new archived column to both tables). Archived issues never show up unless you explicitely
ask for them in the UI.

Last Updated: 11/29/2011 (2.9.04)
/config/ColdSpring.xml.cfm - version
/controller/IssueCOntroller.cfc - fixes a bug when a non-admin switched the project for an issue, found by Andrew


Last Updated: 11/09/2011 (2.9.03)
/config/ColdSpring.xml.cfm - version
/helpers/json.cfc - Added Ben Nadel's cleanHighAsci and added a specific check for vertical tabs.

Last Updated: 8/23/2011 (2.9.02)
/views/pages/issue.cfm - more work on the date picker. If you use a NON American locale and you used Due Date, you will need to fix entries so that they
get re-recorded with the right format - which should be local machine NOT your custom locale. We then display it correctly on the front
end. (Hopefully)
/controller/IssueController.cfc - Oliver Clark updated the HTML email to work correctly in GMail.

Last Updated: 2/9/2011 (2.9.01)
/config/ColdSpring.xml.cfm - version
/config/ColdSpring.xml.cfm - New setting, datepickerdateformat - used to specify a dateformat for the jQuery UI date picker. Read the text in the
config file for details.
/views/pages/issue.cfm - updated to use the new setting

Last Updated: 2/9/2011 (2.9)
/config/ColdSpring.xml.cfm - version
/controller/IssueController.cfc - corrects a bug where we weren't using the dateFormat mask
/controller/UserController.cfc - suppress login errors via rss
/views/exception.cfm - We now suppress errors unless you are logged in as an admin. I'll be coming back to this soon.

MS ACCESS IS NO LONGER SUPPORTED!

Last Updated: 1/4/2011 (2.8)
/config/ColdSpring.xml - version
/views/pages/milestone.cfm and milestonelist.cfm - when you added a new milestone to project N, N wasn't selected by default in the drop down
/views/pages/issuetypes.cfm - typo
/model/StatusGateway.cfc - suggestion to sort by rank AND name
/views/pages/project.cfm - use password field type for password

Last Updated: 12/29/2010 (2.7.9)
/controller/*.cfc - fix for IE/delete issue by Marc,described here: http://lighthousepro.riaforge.org/index.cfm?event=page.issue&issueid=6A02DB16-9747-9179-CE0026445351C4C8
/customtags/datatable.cfm - see above
/model/SeverityBean and StatusBean.cfc - handle passing a non-numeric value to rank
/view/pages/milestone.cfm - support handling no projects
/config/ColdSpring.xml - version

Last Updated: 9/14/2010 (2.7.8)
/controller/UserController.cfc - bug with user save, fix from Rodion Bykov (http://lighthousepro.riaforge.org/index.cfm?event=page.issue&issueid=ACA6EC7C-EF9C-1420-80E57D6548C75AE9)
/config/ColdSpring.xml - version

Last Updated: 9/14/2010 (2.7.7)
/controller/IssueController.cfc - bug with the mail process
/config/ColdSpring.xml - version

Last Updated: 9/10/2010 (2.7.6)
favicon added by Sebastiaan GMC Naafs - van Dijk
/controller/UserController.cfc, /views/viewissues.cfm, /views/exception.cfm: Updated to support a session logout event via Ajax
/config/ColdSpring.xml - version

Last Updated: 8/9/2010 (2.7.5)
WARNING! FLAMING NINJA MONKEYS OF DOOM! READ ME OR PIE WILL BE THROWN AT YOU!!!!

This update includes a database update. Scripts were all updated. The SQL for the MySQL version is given below. There 
is one new table and a modification to lh_milestones to allow for null due dates.

The reason for this update? You can now save displays of issues as filters. Woot. It kicks butt. Give it a try.

/config/ColdSpring.xml - version
/config/ModelGlue.xml - support for filters
/controller/UserController.cfc - ditto
/css/global.css - add color to plain links
/install/ All DB scripts + install guide description of filters. Thanks to Scott Stroz for the MS Access update.
/js/jquery.min.js - updated to jQuery 1.4
/model/UserGateway+Service - support for filters
/views/pages/filters.cfm, viewussues.cfm - ditto
/views/templates/main.cfm - ditto
/controller/* - All controllers were updated to fix a bug w/ multiple selections and deletes.

CREATE TABLE lh_filters  ( 
    useridfk        	varchar(35) NULL,
    projectidfk     	varchar(35) NULL,
    issuetypeidfk   	varchar(35) NULL,
    projectlocusidfk	varchar(35) NULL,
    severityidfk    	varchar(35) NULL,
    statusidfk      	varchar(35) NULL,
    assigneduseridfk	varchar(35) NULL,
    resultcount     	int(11) NULL,
    milestoneidfk   	varchar(35) NULL,
    keywordfilter   	varchar(255) NULL,
    id              	varchar(35) NOT NULL,
    name            	varchar(255) NULL,
    PRIMARY KEY(id)
)
GO

ALTER TABLE `lh_milestones` MODIFY COLUMN `duedate` datetime NULL
GO

=================================== ARCHIVES ===================================

Last Updated: 8/2/10 (2.7.0) 
WARNING! FLAMING MONKEYS OF DOOM! READ ME OR PIE WILL BE THROWN AT YOU!!!!
This update contains a database update. All the install scripts were updated. If you want to run an ALTER statement,
I've included the MySQL version below the list of files updated.

The main purpose of this update is to allow for defaults in projects. You can now default the
area of the bug, the severity, the type, and the status. This applies to new bugs made in the 
interface as well as those received via email.

/config/ColdSpring.xml - version #
/config/ModelGlue.xml - support defaults
/controller/IssueController.cfc and ProjectController.cfc - ditto
/install/ - Scripts + install docs mention of new feature. Thank Scott Stroz for the Access update.
/model/ProejctBean and ProjectGateway - support for defaults
/view/pages/project.cfm - ditto

And now - the SQL script for those who feel like being fancy.

ALTER TABLE `lh_projects`
	ADD COLUMN `defaultlocus` varchar(35) NULL, 
	ADD COLUMN `defaultseverity` varchar(35) NULL, 
	ADD COLUMN `defaultissuetype` varchar(35) NULL, 
	ADD COLUMN `defaultstatus` varchar(35) NULL
GO

Last Updated: 8/2/10 (2.6.8) 
/config/ColdSpring.xml - forgot to add in mailport setting, version #
/controller/IssueController.cfc - support delete severity

Last Updated: 5/17/10 (2.6.7) 
All of the below by Pedro Lopez

/install/oracle.sql - fix by Pedro Lopez
/config/ColdSpring.xml - new setting: dateformat - allows you to specify dateformat display system wide
/model/IssueGateway.cfc - Oracle fix
/views/index.cfm, issue.cfm, milestone.cfm, printissue.cfm, reports.cfm, viewissuesjson.cfm - dateformat support

Last Updated: 5/17/10 (2.6.6) 
/config/ColdSpring.xml.cfm - empty mailpassword field,  version #
/model/MailService.cfc - better handling of mail values - thanks to Lawrence Cramer for helping me get this

Last Updated: 4/21/10 (2.6.5) 
/config/ColdSpring.xml.cfm - version #
/controller/UserController.cfc - Two fixes in save user. First, it was losing the selected email projects for the user. Secondly, if you edited yourself,
it didn't update the session copy.

Last Updated: 3/29/10 (2.6.4) 
/config/ColdSpring.xml.cfm - Just a version #.
/controller/IssueController.cfc - when we email stuff, include project id in link
/controller/UserController.cfc - support going to the desired url when logging in
/views/login.cfm - remember url for after login
/views/projectareas.cfm - Added a bit of text to make it clear this was a system wide setting.

Last Updated: 12/13/09 (2.6.3) 
/config/ColdSpring.xml.cfm - Just a version #.
/config/ModelGlue.xml - save issue action updated to append PID on result.
/controller/IssueController.cfc - When sending an email, prepend subject with "Issue: " and added a colon to Project in FROM name.
/model/IssueGateway.cfc - Fixed a bug where public ID wasn't returned after a save.

Last Updated: 11/11/09 (2.6.2) 
Support for remembering filters was added. Code was written by Bjorn Jensen, but I modified
it heavily to make it fit more into the Model-Glue framework.

/config/ColdSpring.xml.cfm - just a version # change
/config/ModelGlue.xml.cfm - support for remembering filters
/controller/UserController.cfc - support for above
/customtags/datatable.cfm - fixes a stupid IE bug.
/model/IssueGteway.cfc - getIssues returns the creator's name.
/views/pages/report.cfm - shows creator name.
/views/pages/viewissues.cfm - support for remembering filter
/views/templates/main.cfm - ditto above 

Last Updated: 11/11/09 (2.6.1.003) (Updates by Ezra Parker)
/controller/Controller.cfc - fixed a compatibility issue with Open BlueDragon.
/install - Docs updated with instructions for installing on Open BlueDragon.

Last Updated: 10/28/09 (2.6.1.002)
Ignore the 004 below. Brain fart. 
/Application.cfc - added onRequestStart to disable debugging.
/config/ColdSpring.xml.cfm - version
/controller/UserController.cfc - Fixes a bug where updated your preferences could make you lose a project.
/views/ages/rss.cfm - Fixes a bad link and updates to RSS 2.

Last Updated: 10/28/09 (2.6.1.004)
Note - the updates for 10/1/09 were for 2.6.1, I wrote the wrong version #.
/config/ColdSpring.xml.cfm - version
/customtags/renderErrors.cfm - fixed a CF8 array loop to be CF7 compat.
/views/template/main.cfm - fixed a bug when a drop down is used for project display. Thank you Naafs-van Dijk for the find.

Last Updated: 10/1/09 (2.6.004)
/config/ColdSpring.xml.cfm - version
/controller/IssueController.cfc - forgot to write method to handle deleting issue types
/controller/IssueController.cfc - if you delete an attachment and the file doesn't exist, no error.
/controller/IssueControlle.cfc, /model/IssueService.cfc, /model/IssueGateway.cfc, /view/pages/issue.cfm -> Support for deleting issues


Last Updated: 8/20something/09 (2.6.004)
NOTE! Renamed ColdSpring.xml to ColdSpring.xml.cfm.
/config/Application.cfm - added to bounce folks
/index.cfm - support new location of ColdSpring
renamed model/mailService.cfc to MailService.cfc. Case sensitive file systems are a PITA.
docs updated to be more clear about dependancies.

Last Updated: 7/13/09 (2.6.003)
/config/ColdSpring.xml - version
/controller/IssueController.cfc, /helpers/json.cfc, /model/IssueTypeGateway.cfc + MilestoneGateway.cfc + ProjectAreaGateway.cfc + ProjectGateway.cfc + UserGateway.cfc -> Missing var scopes!

Last Updated: 4/27/09 (2.6.002)
/config/ColdSpring.xml - just the version
/controller/IssueController.cfc - handle bug with issue editing from iPhone
/views/projects.cfm - remove the ability for the admin go into the issues - causes a problem if they try to add an issue

Last Updated: 4/27/09 (2.6.001)
issueController.cfc - bad link for email - fix thanks to Mischa Sameli
issueController.cfc - bad code when updating history 
/config/ColdSpring.xml - just the version
/views/pages/viewissues.cfm - link fix

Last Updated: 4/27/09 (2.6)
Every file has been updated. This is a complete (pretty much) rewrite for the Model-Glue 3 framework. Note the following new requirements:

* You must have a modelglue mapping pointing to your ModelGlue 3 install.

* If you do not have ColdFusion 8, you must create a mapping named "lhp" that points to your install folder.

* If you do not have ColdFusion 8, add a custom tag path pointing to the customtags folder under your install.

Note, the unsupported Postgres file was updated by Mark W.

Last Updated: 4/27/09 (2.5.005)
/rss.cfm, /stats.cfm - use right tab in layout
/customtags/layout.cfm - see above
/css/global.css - fix a css item using the wrong image
/components/IssueManager.cfc - fix an issue with sorting by name. Threw an error in SQL Server. Was NOT able to test well, so looking for help confirming.
/defaults.cfm - version

Last Updated: 1/21/09 (2.5.004)
/components/IssueManager.cfc - The Print option would fail on some items if the lookup tables returned null.
/defaults.cfm - version

Last Updated: 12/17/08 (2.5.003)
/stats.cfm - shifted a graph down, helps in smaller resolutions (Sid Wing)
/customtags/layout.cfm - If you have more than 25 projects, the left hand menu switches to a drop down (Brian Love)
/project_view.cfm - Per page is now something you can customize in a drop down (Brian Love)
/defaults.cfm - version

Last Updated: 12/1/08 (2.5.002)
/view.cfm, /customtags/datatables.cfm and layout.cfm -> Martijn van der Woud added JS confirmation on deletes
/view.cfm - fixed bug on attachment upload

Last Updated: 10/21/08 (2.5.001)
view.cfm had bad attachment paths
Docs updated to mention ColdSpring dependancy.
/Application.cfc, /login.cfm - You now see a message if you don't put the right username/password in. Thanks to Dan Vega.
/components/MilestoneDAO.cfc had wrong return type in create (thanks to Dan Parker)
/index.cfm - bug in display of count of open issues (thanks to DP again)
/components/IssueManager.cfc - handles issues that change projects and may not have data in certain fields.
/defaults.cfm - just the version
/issuesjson.cfm - I believe a good international fix
/project_view.cfm - fix a dang IE bug
/view.cfm - support moving issues to new projects

Last Updated: 10/15/08 (2.5.0 Final)
In general, just read the release notes below. I'm going to duplicate the DB changes here though so folks don't miss it.

Modify lh_issues table to add milestoneidfk column. null ok, varchar 35.
Create lh_milestones table:

	id varchar(35)
	name varchar(50)
	duedate date
	projectidfk varchar(35)

Copy all files over.

COLDSPRING is required and should be installed so that /ColdSpring can be found.

Last Updated: 5/30/08 (2.5.0 BETA)
WARNING - BETA - USE AT YOUR OWN RISK
WARNING - PLEASE BACK UP YOUR DATABASE OR WORLDS WILL CRUMBLE

Welcome to LHP 2.5. A lot has changed. I'll make it short and sweet as a proper
blog entry will come when 2.5 Final is released. Basically:

New design by Justin Johnson
jQuery replaced Spry
Issues are loaded one page at a time, not the complete record set.
Issues are more descriptive about changes in their history
Milestones added
ColdSpring REQUIRED now. I used 1.2.
You must manually modify your db. The install scripts are NOT updated. The mod
is simple though. Add a new lh_milestones table:
	id varchar(35)
	name varchar(50)
	duedate date
	projectidfk varchar(35)
	
Then modify lh_issues to add a milestoneidfk column, null is OK, and varchar(35).

mailprocess.cfm was modified by Tjarko Rikkerink. It will now delete mail if it was sent to an address unrecognized by any of the projects. This is a CRITICAL CHANGE and you MUST NOTICE THIS COMMENT! If you use LHP with another database and use the same mail server to listen to bugs, then these emails will be deleted. So in other words, ensure that ONE UNIQUE MAIL ACCOUNT that works with LHP is set up to work with ONE UNIQUE INSTALL of LHP.

view.cfm was also improved by Tjarko. Better handling of history changes in regards to noticing old values of NULL.

Last Updated: 5/30/08 (2.4.7)
user_edit.cfm, status.cfm, severity.cfm, projectloci_edit.cfm, project.cfm, issuetype.cfm: Added MAXLENGTHs to the form fields to prevent users from typing something too long.
/components/ProjectDAO.cfc - removed a CFLOG
index.cfm - I typoed my own blog url.
defaults.cfm - version

Last Updated: 4/30/08 (2.4.6)
Spry 1.6.1 used.

All of the below were sent in by Ron Stewart
/project_view.cfm - Two fixes:
a) Always order print by public ID. I may change this later on to note the sort on the front end.
b) JavaScript fix. I was using $. instead of Spry.$.


Again, thanks to Ron Stewart.

Last Updated: 4/30/08 (2.4.5)
All of the below were sent in by Ron Stewart
/components/IssueManage.cfc - change Loci to Area
/stats.cfm - ditto above, and show bug IDs (the simple values)
/view.cfm - ditto above
/layout.cfm - changes to better support favicon

Last Updated: 4/28/08 (2.4.4)
/Application.cfc - if the attachments folder doesn't exist, try to create it
/defaults.cfm - just the version
/stats.cfm - fixes a bug - I honestly can't remember what it was - but it fixed it. Really. Also change Loci to Area
/customtags/layout.cfm - use Area, not Loci
/index.cfm - minor text fixes
/projectloci_edit.cfm and projectloci.cfm - use Area, not Loci
/project_view.cfm - use Area, Not loci
Fixed the button display (I hope)
You can now filter by Public ID. If you type in 10, it will match on issue 10
/install - Docs updated to talk about 'Areas', not 'Loci'.

Last Updated: 3/13/08 (2.4.3)
Hash Passwords support provided by Jeff Smallwood. 
Ability to disable RSS feeds provided by Jeff Smallwood.
Logo/icon provided by Ron Stewart and Marco Olson.
Bug fix to printing. Before when you printed, it only did the current page in the filter. Not it does all issues in the filter.
JSON.cfc update.

Last Updated: 2/17/08 (2.4.2)
/Application.cfc - remove session timeout
/login.cfm, /view.cfm - I've made it so that if you timeout when editing an issue, when you login, your changes are restored.
/customtags/layout.cfm - missing </li> tags
/includes/udfs.cfm - new tag to help support cleaning bad data

Last Updated: 12/7/07 (2.4.1)
/customtags/layout.cfm - just fixed a footer link
/js/SpryData.js, SpryJSDONDataSet.js, xpath.js - Minimized files
/view.cfm - bad character fix
/project_view.cfm - remember last settings, sorting fixes
/defaults.cfm - version

Last Updated: 7/1/07 (2.4.005)
Switched JSON support. Updated issuesxml.cfm and project_view.cfm.
defaults.cfm updated for version only

Last Updated: 7/1/07 (2.4.004)
/Application.cfc - added json to application scope
/components/json.cfc - JSON support, from:

Authors: Jehiah Czebotar (jehiah@gmail.com)
         Thomas Messier  (thomas@epiphantastic.com)

/layout.cfm - add JSON JS
/defaults.cfm - just version
/index.cfm - for overdue issues, only show where status = open
/issuesxml.cfm - use JSON. I could change the filename, but didn't want to bother.
/js/SpryData.js, /js/xpath.js, /SpryJSONDataSet.js - Spry 1.5 library

Last Updated: 6/15/07 (2.4.003)
/components/IssueManager.cfc - Fixed an issue with trying to save an issue generated by email.
Also made it so Due Date showed up in PDF format.
/defaults.cfm - just version

Last Updated: 6/4/07 (2.4.002)
Will Tomlinson, Jim Wright sent in a MS Access fix for AnnountmentManager.cfc

/defaults.cfm - just version

Docs updated to talk about requirements in access/mysql.

Last Updated: 5/24/07 (2.4.001)
All databases updated. But all for mistakes - so if you are running good, no need to reupdate. 

/rss_view.cfm - Detect port.
/defaults.cfm - just version

Last Updated: 5/18/07 (2.4.001)
Fixes to mysql install script and MS Access db.

Last Updated: 5/12/07 (2.4)

Important note: The database has been updated. A new lh_attachments table has been
created. This table allows for N attachments per issue. You should add this table
to your database. You can either do it by hand, or copy JUST the SQL creation script
for your database. In the install folder you will find a file named update2.4.cfm. 
This file will copy attachment data to the new database. You need to edit it to set
the right DSN. 

IMPORTANT - BACK UP YOUR DB FIRST! I don't expect anything will go wrong, but hey,
you can't be too safe, right? You can also, if you want, drop the attachment column
from lh_issues, but you don't need to.

/Application.cfc - When creating the scheduled task, notice the port.
/announcement.cfm - You can now create announcements with no project.
/components/AnnouncementBean.cfc - allow announcements with no project.
/components/AnnouncementManager.cfc - support for above
/components/IssueBean.cfc -  remove single attachment support
/components/IssueDAO.cfc and IssueManager.cfc - ditto above
/components/toxml.cfc - Curse xmlFormat for not stripping everything it should!
/customtags/layout.cfm - Add + links for Admin options
/defaults.cfm - version
/mailprocess.cfm - support multiple version
/issuesxml.cfm - slim the XML
/project_view.cfm - new call to clean up attachments
/view.cfm - support for N attachments
/install/ All db scripts updated.

Last Updated: 4/19/07 (2.3.004)
/components/IssueManager.cfc - In the HTML email for issues, if there is a related URL, make it hot.
/stats.cfm - Handle issues that have no issuetype, status, etc.
/defaults.cfm - just the version
 
Last Updated: 3/16/07 (2.3.003)
/defaults.cfm - just the version
/rss_view.cfm - nonadmins couldn't view rss links for all my bugs or all projects

Last Updated: 3/16/07 (2.3.002)
/defaults.cfm - just the version
/project_view.cfm - fix silly IE6/7 mistake.

Last Updated: 3/16/07 (2.3.001)
/defaults.cfm - just the version
/install - All database scripts updated. I forgot the new four columns for the changes in 2.3. These changes are in the projects table.

Last Updated: 3/16/07 (2.3)
/defaults.cfm - just the version
/Application.cfm - on startup, create a scheduled task
/mailprocess.cfm - Handles checking email
/project.cfm - new fields for projects
/project_view.cfm - sorting updates for ajax
/view.cfm - remove a dump
/components/Project*.cfc - updates for new mail fields.
/components/IssueManager.cfc - handle unknown values for status/severity/onwer, etc

Last Updated: 2/27/07 (2.2.007)
/defaults.cfm - just the version
/rss_view.cfm - use dynamic titles for the RSS feed
/view.cfm - notice if UUID is valid but not pointing to a valid DB record.

Last Updated: 2/22/07 (2.2.006)
/defaults.cfm - just the version
/project_view.cfm - fix IE caching issue (thanks Douglas Knudsen). Search description in AJAX
/components/projectlocusdao.cfc - sql error
/install/oracle.sql - fix to oracle script

Last Updated: 2/10/07 (2.2.005)
/project_view.cfm - use prettyduedate for proper due date sorting 
/issuesxml.cfm - see above.
/defaults.cfm - version

Last Updated: 2/9/07 (2.2.004)
/index.cfm - Andrew Penhorwood modded the text on the index page. Added a link to riaforge.
/project_view.cfm - AP modded the display a bit. New info shown with filters.
/view.cfm - AP used new windows for links.
/components/IssueManager.cfc - fix to issue where we try to send email to deleted users
/defaults.cfm - version

Last Updated: 1/30.07 (2.2.003)
/project_view.cfm - Restored the ability to only print some issues
/defaults.cfm - just the version again
/stats.cfm - fix bug where user for bug was deleted.

Last Updated: 12/23/06 (2.2.002)
Fixed the gosh darned sql scripts again. 
Thank to dickbob for the Access fix!
/stats.cfm - forgot to fix for issuetypes
/defaults.cfm - just a version change
/components/issuemanager.cfc - access fix and added a column to getissues

Last Updated: 12/20/06 (2.2.001)
Updated mysql.sql,sqlserver.sql - they had bugs in them with the seed data for issuetypes.
Added oracle.sql script.


Last Updated: 12/20/06 (2.2)
Note - many of the changes below are from Qasim Rasheed, specifically support for Oracle, u/p in queries.
Database Updated REQUIRED! - All tables are now prefixed with lh_. You MUST CHANGE YOUR TABLE NAMES!
Please see update2.2.cfm for folks who are upgrading.

/components/AnnouncementDAO.cfc - Support for username/password in query. 
/components/AnnouncementManager.cfc - ditto
/components/IssueDAO.cfc - ditto, remove file for attachment on delete
/components/IssueManager.cfc - ditto, plus slight updates to last set of changes.
/components/ProjectDAO.cfc - ditto
/components/ProjectLocusDAO.cfc - ditto
/components/ProjectLocusManager.cfc - ditto
/components/ProjectManager.cfc - ditto
/components/SeverityDAO.cfc - ditto
/components/SeverityManager.cfc - ditto
/components/StatusDAO.cfc - ditto
/components/StatusManager.cfc - ditto
/components/UserDAO.cfc - ditto
/components/UserManager.cfc - ditto
/components/Utils.cfc - forgot to make it a "real" CFC.
/defaults.cfm - Support username/password fields. New version.
/Application.cfc - new creation logic
/customtags/layout.cfm - Added link to issue types, moved admin links below projects
/issuetypes.cfm, /issuetype.cfm - new files to edit issue types
/view.cfm - support for issue types, nicer pdf link
/status.cfm - removed line that wasn't needed
/issuesxml.cfm - support for ajax
/components/IssueType*.cfc - Initial chekc in


Last Updated: 12/20/06 (2.1.007)
Change to mail again. You CAN use mail server w/o U and P. 
/Application.cfc - implement mail changes.
/stats.cfm - Show due date in Excel report
/IssueManager.cfc - mail changes (again)
/defaults.cfm - just the version updated.
Docs updated to reflect the mail change. (Again)

Last Updated: 12/20/06 (2.1.006)
mailserver cannot be blank. So - if you want to specify a mail server, you MUST also specify a username/password.

/components/IssueManager.cfc - See above
/Application.cfc - ditto
/install - Docs updated to reflect this.

Last Updated: 12/18/06 (2.1.005)
/components/IssueManager.cfc - better handling of text, and Terry added mailserver/port support
/components/Utils.cfc - New file. Note this CFC duplicates the udf from udfs.cfm. Will correct that later.
/defaults.cfm - mailserver/mailport keys. new version
/install/ - Docs updated to talka bout the new keys.

Last Updated: 10/28/06 (2.1.004)
/components/IssueManager.cfc - text emails didn't have a link, links didn't include root
/defaults.cfm - just a version # update

Last Updated: 10/28/06 (2.1.003)
/components/IssueManager.cfc - update to style used in mail, and it now does both plain/html. From Peter Daams.
/defaults.cfm - just a version # update

Last Updated: 10/12/06 (2.1.002)
/components/IssueManager.cfc - slight sql change. 
/components/IssueManager.cfc - Big change to emails. Michael White wrote an HTML version of the bug emails.
/stats.cfm - Use Reports, not Stats. Show creator in excel report.
/rss.cfm - Use Firefox header for RSS links.
/customtags/layout.cfm - Reports, not Stats
/default.xml - just a version update

Last Updated: 9/18/06 (2.1.001)
/status.cfm - typo found by Paul Roe
/default.xml - just a version update

Last Updated: 9/15/06 (2.1)
/components/IssueManager.cfc - port fix in email
/components/Severity and Status CFCs - by Ron Stewart
/customtags/layout.cfm - by Ron Stewart
/stylesheets/gila-screen.css and lhp.css - minor mods by RS
/severities.cfm, /severity.cfm, /statuses.cfm, /status.cfm - by RS
/Application.cfc - support for Status/Severity - by RS
/project_view.cfm, /view.cfm - ditto
/defaults.cfm - new version

Last Updated: 8/22/06 (2.0.6)
/components/IssueManager.cfc - remove extra lines from emails, thanks to Richard Davies
/Application.cfc - no debug output
/defaults.cfm updated for for version
/view.cfm - remove class from file upload box, thanks Richard Davies
/rss_view.cfm - fixed security check, thanks to Grant
/login.cfm - design tweaks, thanks Alan Lanteigne (rkc 8/22/06)
/index.cfm - fixes in stats, thanks to Richard Davies
Documentation typos/fixes by Richard Davies

Last Updated: 6/24/06 (2.0.5)
Fix to components/issuedao.cfc - I didn't properly handle
the first issue in a project
/defaults.cfm updated just for version

Last Updated: 6/22/06 (2.0.4)

VERY IMPORTANT: This update includes both database changes
and a script you MUST run prior to running version 2.0.4.
The change to this version includes two new columns in the
issues table:

publicid (int, can be null)
duedate (date, can be null)

In the install folder you will find a script that will
update your issues table to set a publicid value to each
issue. I HIGHLY recommend you backup your database first.

Because of the large number of files updated, I will not
be listed each one. However, here is an overview of the changes.

Fixed a bug in the links in the quick stats pod on the home page.

Added Due Date and Public ID, which is shown as ID to the public. 

Mails now include extra headers for Outlook. Thanks to Todd Sharp for this enhancement.

Last Updated: 6/16/06 (2.0.3)
SQL files updated. You need to run the code to create Announcements
/components/Announcement*.cfc - new CFCs for Announcements
/components/ProjectDAO.cfc - just a typo in the comments
/customtags/layout.cfm - Design changes by Dan Sorensen
/stylesheets/gila-screen.css - Ditto
/announcement.cfm - announcement editor
/announcements.cfm - announcements editing 
/stats.cfm - A user found a bug where he tried to run stats and had no issues. I couldn't reproduce this but I fixed it for him.
/projects.cfm - Simple text changes
/project.cfm - ditto
/defaults.cfm - version change
/index.cfm - new design by Dan Sorensen

Last Updated: 4/19/06 (2.0.2.104)
/customtags/layout.cfm - dumb me used a full url to my dev environment
/defaults.cfm - made the version # match

Last Updated: 4/19/06 (2.0.2.103)
/customtags/datatable.cfm - htmlEditFormat values
/view.cfm - ditto above
/customtags/layout.cfm - Add a + sign to quickly add bugs. Suggested by Edgar Garcia.

Last Updated: 2/8/06 (2.0.2.102)
Fix to MS Access db, thanks to Birgit (bph@paulisystems.net)
/defaults.cfm - just a version # update

Last Updated: 2/8/06 (2.0.2.101)
/components/IssueManager.cfc - MORE darn fixes related to creator
/view.cfm - Just noticed that when you get errors, they were all on one line
/defaults.cfm - again, just a version # change.

Last Updated: 2/7/06 (2.0.2.100)
/components/IssueBean.cfc - Don't require creatorIDFK (supports old bugs)
/components/IssueManager.cfc - Don't throw a fit if creatorIDFK is blank 
/view.cfm - Ditto above
/defaults.cfm - just updated the version #

Last Updated: 2/7/06 (2.0.2)
/components/IssueBean.cfc - Added Creator logic
/components/IssueDAO.cfc - ditto
/defaults.cfm - Just updated the version.

/components/IssueManager.cfc - support for creator, and many email related changes. People now get
email even when not subscribed, if they are the creator, owner, or old owner. Subjects for emails now include
part of the name.

/install: All db scripts updated to include the 'creatoridfk' field in issues. For those upgrading, you simply
need to add this new column.

Last Updated: 1/31/06 (2.0.1)
/components/IsseManager.cfc - typo in email. Thanks BrianK. Return severityrank.
/components/defaults.cfm - new version key added. Be sure to update your defaults.cfm to copy this value in.
/customtags/datatable.cfm - mod to support severity ranking.
/index.cfm - shows version # now
/view.cfm - just a white space change - therefore I didn't even bother changing the header. Can be ignored.
/install/install.doc updated and PDF version added.

Last Updated: 1/11/06
/project_view.cfm - support for keyword filtering
/projectloci_edit.cfm - syntax error in update
/components/ProjectManager.cfc - new method to get loci for a list of projects
/view.cfm - When editing a new issue, the header wasn't right. Also URL encode attachments. Default bug owner to current user.
/components/UserBean.cfc - allow usernames with dots in them.

Added new unsupported mod - allows for LHP under Oracle and MX 6.1. By Robert Everland III, robert_everland@scps.k12.fl.us
Last Updated: 1/4/06
/install/sqlserver.sql - I forgot the lines that seeded the data! Also, projectloci was using name with length 35, should have been 50
/project.cfm - handle cases with no loci or users selected 

Last Updated: 12/29/05
/project_view.cfm - fixes in filters
/components/IssueManager.cfc - bug in email that went out, would show Bug (Was Bug)

Last Updated: 12/29/05
/view.cfm - changed disabled to readonly
/projectmanager.cfc - sort getProjectsForUser
/install/sqlserver.sql - forgot to update it for attachments
/user_edit.cfm - case fix
/prefs.cfm - error when not picking a project to subscribe to

Last Updated: 12/28/05
Version 2.0
Massive update. Removal of Flash Forms. Various fixes/improvements. The only DB change is the addition of "attachment" do the db. Basically all files
need to be copied from the zip.

Last Updated: 12/2/05
project_view.cfm - fixed relatedurl in Flash Form. Wasn't loading when you clicked to edit.

There is an "unsupported" folder in the install folder. This is for DB scripts not officially supported. I've added
a Postgres SQL file supplied by David Livingston (livingston.dave@gmail.com)

Last Updated: 11/2/05
IssueManager.cfc - lowecased relatedurl in one sql block

Last Updated: 11/1/05
SQL Server install script changed issues.name to have maxlen of 255
IssueManager.cfc returns project name
rss_view.cfm calls right method, and shows project name in title of rss entry

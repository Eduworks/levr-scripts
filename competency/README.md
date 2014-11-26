Competency Web Service LEVR Scripts
==============================

These script files are required for use of the Ontology-Based Competency 
Management Web services.  

* Initially creates a Default Model initially to hold any stray competencies
(these cannot relate to competencies in external models for now)
* Allows Creation of additional Competency Models to store new Competencies in
* Creates User Profile Models to track Competency Records, Validations and
evidence of the validation created by Validation Agents 

Requirements
------------
1. Apache Tomcat Web Server
2. LEVR Server Package (levr-core, levr-base, and eduworks-common repositories)

Installation Instructions:
-------------
1. Create a competency directory in a non-publicy-accessible location on the 
Tomcat server
2. Place the structure-files directory and the Backup/Restore KeyFile in the 
new competency directory
3. Place the RS2 scripts in the /etc directory of the LEVR Tomcat instance. 
4. Create a copy of the libCompetency.config.default file and name it 
libCompetency.config.rs2, this will be the configuration file that is read
5. Change the defaultURI, defaultDirectory, structureDirectory and 
backupRestoreKeyPath configurations in the config.rs2 to match the newly
created locations on the server

**Note:** Currently, the only time that you can change the URI of the server is
before it is first instantiated. Otherwise you will have to delete any existing
models to change it again.

**Finally:** Start the Tomcat server, the API for the Competency Web Services 
should be found at [domain_name or IP address]/levr/api/custom/competency.
After Tomcat has started, their should be 7 new sub-directories in the competency
directory to hold the competency ontologies and database files.

Troubleshooting:
---------------
If you an error occurs during instantiation of the server, or the web service 
calls throw errors right after setup, stop the server and delete all
subdirectories in the competency folder except the structure-files directory.

Ensure that tomcat has read permissions to the RS2 scripts and write 
permissions to everything in the competency directory.

Check for errors in catalina.out in the Tomcat logs directory that may help
pinpoint what is causing them.


# Readme for odbcstack

1. Place the odbcstack.tar.gz tarball into /home/dbadmin (or ~dbadmin if dbadmin's home dir differs)
2. unpack the tarball in dbadmin's home directory with "tar -xvzf odbcstack.tar.gz"
3. cd into the new odbcstack/ directory, and edit the new ".odbc_profile" file
   in ".odbc_profile", edit the section for vsql: 
    * change the VSQL_HOST variable to the name or IP address of your Vertica node
    * change the VSQL_DATABASE variable to the name of your database
    * change the VSQL_PASSWORD variable to your dbadmin password
    normally, these settings can be used by the odb and dbman sections of this profile file
4. source the freshly edited file, with ". .odbc_profile"
5. open the right odbc.ini file with the command "vi $ODBCINI", which also tests if the setting is correct.
6. In that odbc.ini file, 
   * in section [ODBC Data Sources], change the name of the data source to "<your db name> = Vertica database"
   * change the section [vmartdb]: 
     > change [vmartdb] to [<your db name>], 
     > and in the section, change  "Database = vmartdb" to "Database = <your db name>"
     > and also change "Servername = 192.57.222.113" to "Servername = <name or IP address of your Vertica node> "
7. Save and quit odbc.ini
8. go to dbadmin's home directory, and add a last line to ".bash_profile" or ".profile", whichever applies, to contain:
   . $HOME/odbcstack/.odbc_profile
   This ensures you have your ODBC settings loaded every time you log in as dbadmin
Contents of the bin directory - a survival kit:
* cp2all            shell script that copies a file /dir to all Vertica nodes
* d2l               C executable; generates CREATE TABLE from a parsed CSV file
* d2l.exe           same for windows
* dbman             Marco's ODBC based SQL client; powerful output formatter and code generator; and yes, SQL command interpreter
* dbman.exe         same for windows
* ep.pl             parameter marker expander. Takes a query template with ${param} markers; expands them using a parameter file
* fmtmsecs          formats milliseconds to D HH:MI:SS.FFFFF format
* fmtsecs           formats seconds to D HH:MI:SS.FFFFF format
* odb               Maurizio's ODBC based client; multi-threaded query driver and data mover; and yes, SQL command interpreter
* odb.exe           same for windows
* odb64luo          same as odb
* odbmon-0.5.1.pl   perl script to monitor long running odb copy commands
* onall             shell script that executes the command passed as parameters on all nodes
* qprof             symbolic link to newest qprof script 
* qprof-0.4c.sh     previous qprof script
* qprof-0.4d.sh     newest qprof script 
* sprof             symbolic link to newest sprof script
* sprof-0.2e.sh     previous sprof script 
* sprof-0.4a.sh     previous sprof script 
* sprof-0.4e.sh     previous sprof script 
* sprof-0.4f.sh     current  sprof script 


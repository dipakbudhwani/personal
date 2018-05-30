Oracle connectivity for node.js.

Full installation guide:  https://github.com/oracle/node-oracledb/blob/master/INSTALL.md#github 

Command to install using python path and oracle package path:
npm install --python=/whereever/python-2.7/bin/python c:/oracle/C:\Users\db3655\Downloads\node-oracledb-master


https://github.com/oracle/node-oracledb    source code for oracledb package.

Download odpi zip from https://github.com/oracle/odpi and extract in odpi folder in node-oracledb-master downloaded earlier from https://github.com/oracle/node-oracledb

Basic Requirement: 
1.	oracle instantclient Basic download from http://www.oracle.com/technetwork/topics/winx64soft-089540.html  then set its location to PATH environment variable.(it uses oci.dll file)
2.	Python 2.7: download from https://www.python.org/downloads/
3.	Oracle instant client 11.2 will need Visual Studio 2005 redistributable 
Example to connect:
var oracledb = require('oracledb');
oracledb.getConnection(
  {
    user          : "PMOPORTAL_SID",
    password      : "jan@abc",
    connectString : "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=t1pmo1d6.vci.att.com)(PORT=1524))(CONNECT_DATA=(SID=t1pmo1d6)))"
  },
  function(err, connection)
  {
    if (err) { console.error(err); return; }
    connection.execute(
      "select * from t_errorlog",
      function(err, result)
      {
        if (err) { console.error(err); return; }
        console.log(result.rows);
      });
  });





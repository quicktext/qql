# The Syntax Tree Anaylsis

```abnf
parse = (qql/qml) *(SEMI (qql/qml)) [SEMI] EOF;

qml =  VACUUM / DELETE corpuses / CLEAN corpuses;

qql = queryStmt whereStmt [processStmt] whichStmt licenseStmt;

queryStmt = SELECT queryFields FROM corpuses;

queryFields = field  *(COMMA field);

field = STRING;

corpuses = corpus *(COMMA corpus);

corpus = coprusStmtKey;

whereStmt = WHERE keywordStmt [COMMA limitStmt] [COMMA updateStmt];

keywordStmt = KEYWORD COMMANDASSIGN LSBRACKET keyword RSBRACKET;

keyword = keywordStmtValue *(COMMA keywordStmtValue);

keywordStmtValue = STRING;
   
processStmt = [doStmt] [withStmt] [whenStmt];   

whichStmt = WHICH whichInputStmt [whichOutputStmt];

whichInputStmt = schemaStmt COMMA csStmt;
   
whichOutputStmt = [COMMA psStmt] [COMMA modelStmt];
   
schemaStmt = SCHEMA COMMANDASSIGN LSBRACKET schemaStmtList RSBRACKET;

schemaStmtList = schemaStmtMap *(COMMA schemaStmtMap) ;

schemaStmtMap = schemaStmtKey COMMANDASSIGN schemaStmtValue;

schemaStmtKey = STRING;

schemaStmtValue = STRING;

modelStmt = MODEL COMMANDASSIGN LSBRACKET modelStmtList RSBRACKET;

modelStmtList = modelStmtMap *(COMMA modelStmtMap);

modelStmtMap = modelStmtKey COMMANDASSIGN modelStmtValue;

modelStmtKey = STRING;

modelStmtValue = STRING;

csStmt = CORPUS COMMANDASSIGN LSBRACKET coprusStmtList RSBRACKET;

coprusStmtList = coprusStmtMap *(COMMA coprusStmtMap);

coprusStmtMap = coprusStmtKey COMMANDASSIGN coprusStmtValue;

coprusStmtKey = STRING;

coprusStmtValue = STRING;

psStmt = PLUGIN COMMANDASSIGN  LSBRACKET pluginStmtList RSBRACKET;

pluginStmtList = pluginStmtMap *(COMMA pluginStmtMap);

pluginStmtMap = pluginStmtKey COMMANDASSIGN pluginStmtValue;

pluginStmtKey = STRING;

pluginStmtValue = STRING;

dsStmt = DAEMON COMMANDASSIGN LSBRACKET daemonStmtList RSBRACKET;

daemonStmtList = daemonStmtMap *(COMMA daemonStmtMap);

daemonStmtMap = daemonStmtKey COMMANDASSIGN daemonStmtValue;

daemonStmtKey = STRING;

daemonStmtValue = STRING;
   
licenseStmt = COMMA LICENSE COMMANDASSIGN LSBRACKET licenseStmtList RSBRACKET;

licenseStmtList = licenseStmtMap *(COMMA licenseStmtMap);

licenseStmtMap = licenseStmtKey COMMANDASSIGN licenseStmtValue;

licenseStmtKey = STRING;

licenseStmtValue = STRING;
   
whenStmt = WHEN [cronStmt] [COMMA dsStmt];

cronStmt = CRON COMMANDASSIGN LSBRACKET cronStmtValue RSBRACKET;

cronStmtValue = STRING;

limitStmt = LIMIT limitStart COMMA limitOffset;

limitStart = NUMBER;

limitOffset = NUMBER;

updateStmt = UPDATE COMMANDASSIGN updateType;

updateType = UPDATELAZY / UPDATELOCAL / UPDATEREMOTE;

doStmt = DO (sortStmt / filterStmt) *(COMMA (sortStmt / filterStmt));

sortStmt = SORT COMMANDASSIGN LSBRACKET sortStmtMap *(COMMA sortStmtMap) RSBRACKET;

sortStmtMap = sortStmtKey COMMANDASSIGN sortStmtValue;
   
sortStmtKey = STRING;
   
sortStmtValue = ASC / DESC;

filterStmt = [BLACK] FILTER COMMANDASSIGN LSBRACKET filterStmtMap *(COMMA filterStmtMap) RSBRACKET;

filterStmtMap = filterStmtKey COMMANDASSIGN filterStmtValue;

filterStmtKey = STRING;
 
filterStmtValue = STRING;

withStmt = WITH pluginsStmt;

pluginsStmt = PLUGINS COMMANDASSIGN LSBRACKET pluginsStmtList RSBRACKET;

pluginsStmtList = pluginsStmtMap *(COMMA pluginsStmtMap);

pluginsStmtMap = pluginsStmtKey COMMANDASSIGN pluginsStmtValue ;

pluginsStmtKey = pluginStmtKey;

pluginsStmtValue = STRING;
```

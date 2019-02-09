# Comparisons of the Quicktext Query Language (QQL) and Structure Query Language (SQL)

By Genix

# Similarities of the two languages
1. Both are insensitive;
2. Both are used for data management;

# Differences of definitions
|  QQL  | SQL |  
|- | :- | 
| CORPUS | TABLE | 
| CORPUSES | DATABASE |

# Differences of Data Definition Language (DDL)

## Differences of lexical analysis

| Name | QQL  | SQL |  
|-| :-: | :-: | 
|CREATE | Supported, but maintained automatically and invisible to users | Supported and maintained by the program | 
|ALTER| Not supported | Supported and maintained by the program | 
|DROP| Supported and maintained by the program and visible to users  | Supported and maintained by the program |
|TRUNCATE| Not supported | Supported and maintained by the program | 
|COMMENT| Not supported | Supported and maintained by the program | 
|RENAME| Not supported | Supported and maintained by the program | 

# Differences of Data Control Language (DCL)

## Differences of lexical analysis
| Name | QQL  | SQL |  
|-| :-: | :-: | 
|CREATE| Not supported directly | Supported and maintained by the program | 
|DROP| Not supported directly| Supported and maintained by the program | 
|SET| Not supported directly| Supported and maintained by the program | 
|REVOKE| Not supported directly | Supported and maintained by the program | 
|GRANT| Not supported directly| Supported and maintained by the program | 

The QQL **doesn't support all the data control language directly** because the authorization is granted by tokens rather than by local commands.

## Additional keywords of the Quicktext Query Language (QQL)
1. WHICH
2. SCHEMA
2. CORPUS
3. PLUGIN
4. MODEL
5. DAEMON
6. CERTIFICATE

# Differences of Data Manipulation Language (DML)

## Differences of lexical analysis
| Name | QQL  | SQL |  
|-| :-: | :-: | 
| INSERT | Supported, but maintained automatically, and invisible to users| Supported and maintained by the program| 
| UPDATE | Supported, but maintained automatically, and visible to users| Supported and maintained by the program| 
| DELETE | Supported and maintained by the program, and visible to users | Supported and maintained by the program| 
| MERGE | Not supported | Supported and maintained by the program | 
| CALL |  Not supported directly, but supported in other keywords| Supported and maintained by the program | 
| EXPLAIN PLAN| Not supported directly, but replaced by keyword *cron* | Supported and maintained by the program | 
| LOCK TABLE| Not supported | Supported and maintained by the program | 

## Additional keywords of the Quicktext Query Language (QQL)

1. WHEN
2. CRON
3. UPDATE (The UPDATE keyword in QQL and QQL is **not the same meaning**! UPDATE keyword only have three types: LAZY, LOCAL and REMOTE!)
4. DELTEE (The DELETE keyword in QQL and QQL is **not the same meaning**!)
5. CLEAN
6. VACUUM

# Differences of Data Query Language (DQL)

## Differences of lexical analysis
| Name | QQL  | SQL |  
|-| :-: | :-: | 
|SELECT| Supported | Supported | 
|DISTINCT| **Not supported** | Supported | 
|AND| **Not supported** | Supported | 
|OR| **Not supported** | Supported | 
|LIKE| **Not supported** | Supported | 
|FROM| Supported | Supported | 
|WHERE| Supported | Supported | 
|SHOW| Supported | Supported | 
|HELP| Supported | Supported | 
|GROUP BY| **Not supported** | Supported | 
|HAVING| **Not supported** | Supported | 
|ORDER BY| **Not supported directly**, but supported in other keywords | Supported | 
|LIMIT| Supported | Supported | 

The QQL **doesn't support keyword 'LIKE'** because the querying mechanism is similar to K-V querying.

## Additional keywords of the Quicktext Query Language (QQL)

1. DO
2. SORT 
3. FILTER
4. BLACK FILTER

# Differences of Data Transaction Language (DTL)

## Differences of lexical analysis
| Name | QQL  | SQL |  
|-| :-: | :-: | 
|START TRANSACTION| Not supported directly | Supported and maintained by the program | 
|SAVEPOINT| Not supported directly| Supported and maintained by the program | 
|COMMIT| Not supported directly | Supported and maintained by the program | 
|ROLLBACK| Not supported directly | Supported and maintained by the program | 
|TO SAVEPOINT| Not supported directly | Supported and maintained by the program | 

The QQL **doesn't support all the data transaction language directly** because the transaction is for high performance.

## Additional keywords of the Quicktext Query Language (QQL)

1. PLUGINS

# Samples
# The content of _demo.sql_

```
LINE1: select 'title','author','abstract','url','keyword'
LINE2: from 'cssci','cscd','patent'
LINE3: where keyword like '%media%'
LINE4: AND keyword like '%AI%'
LINE5: AND keyword like '%AI%media%'
LINE6: order by title asc
LINE7: limit 0,1000
```
# The content of _demo.qql_

```
LINE1: select 'title','author','abstract','url','keyword'
LINE2: from 'cssci','cscd','patent'
LINE3: where keyword=['media','AI','AI+media'] 
LINE4: when cron=['0,0,0,0,0,0,0']
LINE5: limit 0,1000 
LINE6: update = cache 
LINE7: do sort = ['year' = asc,'name' = asc],
LINE8: filter = ['name' = 'information','year' = 'analytics'],
LINE9: black filter = ['name'='data','year'='research']
LINE10: with plugins=['mail'='genix@quicktext.cn','sms'='+8600000000000']
LINE11: which schema=['schema://username:password@schema.quickcopus.cn/ris/token1'], 
LINE12: model=['tensorflow'='D:/google.model','caffe'='C:/berkery.model'],
LINE13: corpus=['cssci://username:password@corpus.quickcopus.cn/cssci/token1',
LINE14:         'cscd://username:password@corpus.quickcopus.cn/cscd/token2',
LINE15:         'patent://username:password@corpus.quickcopus.cn/sci/token3'],
LINE16: plugin=['mail://username:password@action.quickcorpus.cn/mail/token4',
LINE17:       	'sms://username:password@action.quickcorpus.cn/sms/token5'],
LINE18: daemon=['daemon://username:password@daemon.quickcoprus.cn/cron/token6',
LINE19: 		    'daemon://username:password@daemon.quickcoprus.cn/cron/token7',
LINE20:     	  'daemon://username:password@daemon.quickcoprus.cn/cron/token8']
LINE21: certificate=['certificate://licence.quickcoprus.cn/UUID']
```	

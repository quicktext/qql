# Comparisons of the QQL and the SQL

# Similarities
1. Both are insensitive;
2. Both are used for data management;

# Differences of definitions
|  QQL  | SQL |  
|- | :- | 
| OBJECT | RECORD | 
| CORPUS | TABLE | 
| CORPUSES | DATABASE |

The QQL is oriented to the corpuses while the SQL is oriented to the database.

In another word, the QQL is a NOSQL language.

# Differences of Data Definition Language (DDL)

The DDL of the SQL includes CREATE, ALTER, DROP, TRUNCATE, COMMENT and RENAME statements while the QQL does not support the DDL.

The QQL need not the DDL because the QQL defines the data automatically.

# Differences of Data Control Language (DCL)

The DCL of the SQL includes CREATE, DROP, SET, REVOKE and GRANT statements while the QQL does not support the DCL.

The QQL need not the DDL because the QQL maintains the permissions automatically by the authorization servers.

The kinds of the authorization servers:

1. SCHEMA server
2. CORPUS server
3. MODEL server
4. VISUALIZATION server
5. LICENSE server

# Differences of Data Manipulation Language (DML)

The DML of the SQL includes INSERT, UPDATE, DELETE, MERGE, EXPLAIN PLAN and LOCK TABLE statements while the QQL does not support the DML.

The QQL need not the DDL because the QQL maintains the data automatically.

To delete the data, you can delete the data folder directly.

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
|GROUP BY| **Not supported** | Supported | 
|HAVING| **Not supported** | Supported | 
|ORDER BY| **Not supported directly**, but supported in other keywords | Supported | 
|LIMIT| Supported | Supported | 

The QQL **doesn't support keyword 'LIKE'** because the querying mechanism is similar to K-V querying.

If you want to sort the data, you need index the data firstly then load the model.

## Additional keywords of the Quicktext Query Language (QQL)

1. DO
2. MODEL 
3. FILTER
4. BLACK FILTER
5. PRORCESS

# Differences of Data Transaction Language (DTL)

The DTL of the SQL includes 'START TRANSACTION', 'SAVEPOINT, COMMIT', 'ROLLBACK' and 'TO SAVEPOINT' statements while the QQL does not support the DML.

The QQL need not the DTL because the QQL maintains the data transaction automatically.


## Additional keywords of the Quicktext Query Language (QQL)

1. VISUALIZATION
2. MODEL
3. CORPUS
4. LUCENSE

# A full QQL demo

```SQL
select 
	'title','author','abstract','url'
from
	'cssci','cscd','patent'
where 
	keyword=['media','AI','AI+media'],
	limit 0,1000,
	update = local 
do 
	test=[
		'lucene1.sort.year' = 'desc',
		'lucene1.sort.name' = 'asc',
		'tensorflow2' = 'cscd',
		'caffe2' = 'cscd'
		],
	filter = [
		'name' = 'information',
		'year' = 'analytics'],
	black filter = [
		'name'='data',
		'year'='research']
with	
	visualize=[
		'mail'='genix@quicktext.cn',
		'sms'='+8600000000000',
		'csv'='1.csv',
		'ris'='2.ris']
which 
	schema=[
		'cssci'='http://www.quicktext.cn/ris?eeaeb365bb7a45cbb1f8773d63ead0fc',
		'cscd'='http://www.quicktext.cn/ris?bda02d1d34cd45fc9ce3f1d05e2dde57'], 
	corpus=[
		'cssci'='http://cssci.doi.ai/json?q=',
		'cscd'='http://cscd.doi.ai/json?q=',
		'patent'='http://username:password@corpus.quickcopus.cn/sci/token3'],
	testmodel=[
		'tensorflow1'='D:/google.model',
		'caffe2'='C:/berkery.model',
		'lucene3'='C:/index_dir1/'],
	trainmodel=[
		'tensorflow4'='D:/google.model',
		'caffe5'='C:/berkery.model',
		'lucene6'='C:/index_dir1/'],
	visualization=[
		'mail'='http://username:password@action.quickcorpus.cn/mail/token4',
		'sms'='http://username:password@action.quickcorpus.cn/sms/token5'],
	license=[
		'license'='http://www.quickcoprus.cn/debug.qprivate']
```

# A simple QQL demo
```SQL
select 
	'title','author','abstract','url'
from
	'cssci'
where 
	keyword=['media']
which 
	schema=[
		'cssci'='http://www.quicktext.cn/ris?eeaeb365bb7a45cbb1f8773d63ead0fc'], 
	corpus=[
		'cssci'='http://www.doi.ai/json?q=']
```
    

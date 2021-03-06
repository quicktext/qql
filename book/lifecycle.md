# The lifecycle differences between QQL and SQL

> The SQL filename: _demo.sql_ 

There are seven statments in _demo.sql_.

> The QQL filename: _demo.qql_

There are 21 statments in _demo.sql_.

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

# The lifecycle overview of the SQL

I take the [SQLite](http://www.sqlite.org) for example.

![Sqlite life cycle](https://sqlite.org/images/vfs1.gif)

1. The Tokenizer
2. The Parser
3. The Code Generator
4. The Byte code generator
5. The Virtual Machine module
6. The B-Tree module
7. The Pager module
8. The OS Interface 

> The full text is cited form <https://sqlite.org/vfs.html>
> 1. The internal organization of the SQLite library can be viewed as the stack of modules shown to the right. 
> 2. The Tokenizer, Parser, and Code Generator components are used to process SQL statements and convert them into executable programs in a virtual machine language or byte code. 
> 3. The byte code generated by the top three layers is a prepared statement. 
> 4. The Virtual Machine module is responsible for running the SQL statement byte code. 
> 5. The B-Tree module organizes a database file into multiple key/value stores with ordered keys and logarithmic performance. 
> 6. The Pager module is responsible for loading pages of the database file into memory, for implementing and controlling transactions, and for creating and maintaining the journal files that prevent database corruption following a crash or power failure. 
> 7. The OS Interface is a thin abstraction that provides a common set of routines for adapting SQLite to run on different operating systems. 


# The lifecycle overview of the QQL

I take the [Quickcorps](http://www.quickcorpus.cn) for example.

![Quickcorps life cycle](../images/qqllifecycle.png)

1. The Tokenizer
2. The Parser
3. The B-Tree module
4. The Pager module
5. The OS Interface 

Quickcorps doesn't have the following steps.

1 ~~The Code Generator~~

2 ~~The Byte code generator~~

3 ~~The Virtual Machine module~~

Because the current Quickcorpus is written in Java Programming, the Java Programming is cross platform.

# References

1. [File Database File Format](https://sqlite.org/fileformat2.html)
2. [The SQLite Bytecode Engine](https://sqlite.org/opcode.html)

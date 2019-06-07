# Welcome to the Quicktext Query Language

Quicktext Query Language is called the QQL for short.

Quicktext Query Language is a new DSL language designing for the QuickCoprus.

QuickCoprus is a new **NOSQL** database.

We have added patent database: <http://www.wepd.org/>

We have added paper database: <http://www.doi.ai/>

We have added main website: <http://www.quicktext.cn/>

# News

2019.5.5 We have added patent database: <http://www.wepd.org/>

2019.3.27  The data server is updating , it will be restarted on May 1, 2019.

2019.3.15    Version 0.0.4 Release! 

Windows Terminal URL: <https://github.com/quicktext/qql/releases/tag/v0.0.4>

Web Terminal Demo URL: <http://www.quicktext.cn/QQLTerminal/>

![0.0.3](images/0.0.3.png)

DEBUG KEY Download: <http://www.quicktext.cn/debug.qprivate>

# A simple demo:

```SQL
select 	'title','author','abstract','url' from	'cssci','cscd'
where keyword=['media','AI','AI+media']
which schema=[
		'cssci'='http://www.quicktext.cn/ris?eeaeb365bb7a45cbb1f8773d63ead0fc'], 
	corpus=[
		'cssci'='http://cssci.doi.ai/json?q=']
```


# A full demo:

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

# About Quicktext Query Language

The [***Quicktext Query Language***](http://www.quicktext.org) is called [***QQL***](http://www.quicktext.org) for short. 

On the other hand, the ***Structure Query Language*** (***SQL***) is a widely used programming language in the database.

The ***QQL*** is a domain-specific language oriented to the ***corpus processing***, while the ***SQL*** is oriented to the ***data processing***.

Although the corpus processing belongs to the data processing, yet there are many differences in the processing.

The principle of the QQL is under the ***CAP*** theory while the principle of the SQL is under the ***ACID*** theory.

# Copyrights

All the ***QQL***, ***QuickCorpus*** and ***QuickVIZ*** were developed by Genix independently when he began working in Quicktext Infotech Co., Ltd. They are the products of ***Quicktext Infotech Co., Ltd***.

For ***non-commercial use***, please under the license of the ***MIT license***.

For ***commercial use***, please contact the Quicktext Infotech Co., Ltd to register a ***license***.

# The family of the Quicktext Query Language (QQL)
- [x] [QQLCloud](http://www.qqlclod.com/): The cloud storage for QQL users.
- [x] [QQLHub](http://www.qqlhub.com/): The hub for QQL development.
- [x] [QQLstudio](http://www.qqlstudio.com/): The IDE for QQL developers.
- [x] [QQLVIZ](http://www.qqlviz.com): The data visualization toolkits.
- [x] [QQLModel](http://www.qqlmodel.com): The data modelization toolkits
- [x] [QuickCorups](http://www.quickcorpus.org/): A server implements of the QQL standard
- [x] [QuickFS](http://www.quickfs.org/): The File System of the QQL
- [x] [QQL](http://www.quicktext.org/): The specification of the Quicktext Query Language.

# The comparison tables between the QQL and SQL.
- [x] [The comparison table between the SQL and the QQL](book/comparisons.md)
- [x] [The loading mechanism comparison table](book/tutorials.md)
- [x] [The life cycle comparison table](book/lifecycle.md)
- [x] [The module comparison table](book/modules.md)
- [x] [The comparison table of the indexer design](book/indexer.md)

# Documents
## Documents for beginners
- [ ] The user manual
- [x] [The demo scripts of the QQL](book/qql.demo.md)
- [x] [Frequently Asked Questions](faq.md)
- [x] [Download the QQL Terminal v0.0.2](https://github.com/quicktext/qql/releases)
- [x] [ChangeLog of v0.0.2](changelog.md)
- [x] [Specification of Quicktext Query Language](specification.md)
- [x] [Other Languages](otherlanguage.md)

## Documents for designers of QQL compiler
- [x] [The lexical analysis](book/qql.lexer.md)
- [x] [The syntax tree analysis](book/qql.parser.md)
- [x] [How to take part in designing the compiler?](how.md)
- [x] [Quicktext Query Language Reference](references.md)

# About Genix

Genix is a ***Java*** coder. He began learning Java Programming since ***2003***. 
# Contact Genix

***Only*** reply for ***technology*** questions, other questions ***please contact with the company***!
 
Genix's email: ***genix@quicktext.cn***

Genix ***doesn't*** use any social instant messages such as the ***Wechat*** and ***Telegram***, ***only*** use the email!

# Contact Company (For any questions)

Company website: <http://www.quicktext.cn>

Genix's twitter (***maintained by the company***): [@realGenix](https://twitter.com/realGenix)

## **China**

Mr Ding 

E-mail: alex@quicktext.cn

QQ: 635512001

Wechat: 18652029400

Mobile: 18652029400

## **For Other countries**

Mr Li 

Business manager 

E-mail: you.li@quicktext.cn

QQ: 1169195645

Wechat: LY10184712

Mobile: 13125091018


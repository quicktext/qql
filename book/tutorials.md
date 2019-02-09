# Tutorials of the QQL!

The Quicktext Query Language includes two parts:
1. The Corpus Query Language (CQL) of the Quicktext Query Language (QQL)
2. The Corpus Control Language (CCL) of the Quicktext Query Language (QQL)

QQL is ___not___ a case-sensitive language.

In this section, I will give some demos for learning the CCL of the QQL.

The demos are written in the Java Language, but you can use any other languages as well.

# DEMO1: The simplest CQL statement
## File.1  _CQL1.qql_
```SQL
select 'title','author','abstract','url' from 'cssci'
where keyword=['doc2vec'] 
which 
	schema=[
		'schema://username:password@schema.quickcopus.cn/ris/schematoken'], 
	corpus=[
		'cssci'='http://username:password@corpus.quickcopus.cn/sci/corpustoken'],
	license=[
		'license'='http://licence.quickcoprus.cn/token']
/*If you run on the web terminal of the www.quickcorpus.cn then you don't need a license!*/;
```
## Description of File.1

1. The simplest statement includes three essential statements:
   1. The query statement:  ```select 'title','author','abstract','url' from 'cssci'```

   ```'title','author','abstract','url'``` are called ```query _fileds_```, and ```cssci``` is called ```query _corpus_```.
   
   2. The where statement: ```where keyword=['doc2vec'] ```
   
   ```doc2vec``` is the ```query keyword```.
   
   3. The which statement: ```which schema=['schema://username:password@schema.quickcopus.cn/ris/tokenSchema'], corpus=['cssci'='http://username:password@corpus.quickcopus.cn/cssci/tokenCssci'],license=['license'='http://licence.quickcoprus.cn/tokenLicence']```
    
    The keyword ```schema``` indicates the schema of the query object. All the ```query fileds``` must belong to the query object.

   The value of schema includes the _schema protocol_ ```schema://```, _schema server URL_ ```username:password@schema.quickcopus.cn```,  _schema class_ ```ris``` and _schema token_ ```tokenSchema```. The Token values are commonly [UUID](https://en.wikipedia.org/wiki/UUID) values.

    The keyword ```corpus``` indicates the source of the corpus servers. The corpus statement includes a series of [Maps](https://en.wikipedia.org/wiki/Hash_table). The key of the map is ```cssci```, and the value of the map is ```http://username:password@corpus.quickcopus.cn/cssci/tokenCssci```. 
   

2. Constraint:
   1. In this statement, we can download the data from the corpus server according to the which statement. 
   2. If you run on the web terminal of the www.quickcorpus.cn then you don't need a license!

## Figure.1 The life cycle of the QQL

![Quickcorps life cycle](../images/qqllifecycle.png)

## Figure.2 The abstract syntax of _CQL1.qql_

![The abstract syntax tree of CCL1](../images/ccl1_ast.png)

## Description of Figure.1 and Figure.2

The life cycle of the QQL includes five steps:
1. The Tokenizer
2. The Parser
3. The B-Tree module
4. The Pager module
5. The OS Interface 

In the ```step 1``` and ```step 2```, the program will parse the abstract syntax tree in the Figure.2

Before the ```step 3``` , the program will validate the license, schema and cached corpus according to the validating decision table.

## The validating decision table.

1. Validating the license token and corpus token:
   1. Is the license token valid? 
      1. If no, the program will exit and show an error message;
      2. If yes, the program continues executing.
   2. Is the corpus token valid? 
      1. If no, the program will exit and show an error message;
      2. If yes, the program continues executing.
2. Validating the schema.
   1. The schema is a valid [JSON](https://en.wikipedia.org/wiki/JSON) file.
   2. The json file will be downloaded in the ```cache``` folder with the file name ```'class_token.json'```, such as ```'ris_204c837db67e462987595675a78c7eca.json'```.
   3. Generate the [Data Transfer Object (DTO)](https://en.wikipedia.org/wiki/Data_transfer_object) according to the json file. The name of the DTO is class_tokenSchema.class, such as ```'Ris_204c837db67e462987595675a78c7eca.class'```. The generator is based on the [ASM](https://asm.ow2.io/) library. The DTO class will be saved in the 'cache' folder.
   4. Load the DTO class in the memory.
3. Validating the cached corpus file (Coprus file uses the extension '.qcf'.):
   1. The default token validation program used the corpus token, such as the ```'tokenCssci'```. 
      If failed, the program will request a new token by the username and password ignoring the corpus token in the statement. 
      Is the corpus token valid? 
      1. If no, the program will exit and show an error message;
      2. If yes, the program continues executing.
   2. Is there a file called the ```'schema_schemaToken_corpus_corpusToken.qcf'```? 
      For example, is there a file called ```'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd.qcf'```?
      1. If no, it indicates that there is no cached corpus now;
      2. If yes, the 'qcf' is the cached corpus file.
 
## Figure.3 The validating decision table diagram
 
## Initialize the cache corpus. 
 
1. If 'qcf' file is existed, then the program will load the 'qcf' file.
2. If 'qcf' file is not existed, then the program will create the 'qcf' file in the background.

In the second situation, the program will complete a series of processes. All the processes are invisible to the users:
1. Executing the Coprus Control Language (CCL) in the background automatically: 
```SQL
CREATE CORPUSES 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd';
CREATE CORPUS 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_url'
CREATE CORPUS 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_meta'
CREATE CORPUS 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_fulltext'
```
After these three steps, there is a file called 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd.qcf' in the 'cache' folder.

There are three corpuses in the 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd.qcf' file: 
1. URL CORPUS: storing the corpus server addresses with the corpus name 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_url'
2. META CORPUS: storing the corpus fields 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_meta'. The definitions come from the corpus schema.
3. FULLTEXT CORPUS: storing the full text of the corpuses with the corpus name 'Ris_204c837db67e462987595675a78c7eca_cssci_6b9146da656448b89ae024d395f399fd_fulltext'. The FULLTEXT CORPUS doesn't index the data directly, this is **a very important difference** when compared to SQL databases!

All the identifiers are using the UUID. For every corpus.
The data structure of these corpuses contains a B+ Tree and a B* Tree.
If you want to understand the principles of the B+ Tree and the B* Tree, please read the chapter 11 of the book ['Essential Algorithms'](http://shop.oreilly.com/product/9781118612101.do) by Rod Stephens.
On the other hand, the Quickcorpus doesn't lock the file and support the transaction in the file layer for high performance. This is **another very important difference** when compared to SQL databases!

2. Executing the Corpus Manipulation Language (CML) in the background automatically: 
Although the CML doesn't design the 'INSERT STATEMENT', yet the following steps are similar to the SQL procedure.
```SQL
INSERT INTO TABLE URL CORPUS VALUES (?,?,?...?);
INSERT INTO TABLE URL CORPUS VALUES (?,?,?...?);
INSERT INTO TABLE URL CORPUS VALUES (?,?,?...?);
```
**We don't design the 'insert' statement because the inserting mechanism of the QQL and SQL are totally different!**

For the SQL, it's following the [ACID](https://en.wikipedia.org/wiki/ACID) theory; however, the QQL is following the [CAP](https://en.wikipedia.org/wiki/CAP_theorem) theory.

1. URL CORPUS
Send a request to the corpus servers with arguments 'keywords'. 

For example, send a request URL like ```'http://cssci.doi.ai/json/?q=(content:doc2vec)'```. 

Then return the total size of the records from the remote server. 

According to our experiences, we design the minimum batch task number is ***one hundred***. 

We called one hundred record a task and a task group contains many tasks.

We design this mechanism is for multithreading fetching.

The URL corpus is used to record the fetching states. The states include the init state, fetching state, completed state and error state.

2. META CORPUS
After fetching a task from the URL CORPUS, then program run a the fetching thread.

When a task has set up, the program will change all the init state in the URL corpus to fetching state.

One the other hand, the program will fetch the corpuses from the remote servers according to the corpus schema excuse a special field "fulltext".

The meta corpus fetching thread is **synchronous** in a task.

The filed 'fulltext' will be processed in the FULLTEXT CORPUS, not in the META CORPUS.

Aftering storing the meta corpus, the program will change the state in the URL corpus.

3. FULLTEXT CORPUS

The FULLTEXT CORPUS continues fetching the full-text corpus and storing in the FULLTEXT CORPUS.

The fulltext corpus fetching thread is **asynchronous**.

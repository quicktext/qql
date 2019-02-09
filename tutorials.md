# Hello World from QQL!

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
/*If you run on the web terminal of the www.quickcorpus.cn then you don't need a licence!*/;
```
## Description of File.1

1. The simplest statement includes three essential statments:
   1. The query statement:  ```select 'title','author','abstract','url' from 'cssci'```

   ```'title','author','abstract','url'``` are called ```query _fileds_```, and ```cssci``` is called ```query _corpus_```.
   
   2. The where statement: ```where keyword=['doc2vec'] ```
   
   ```doc2vec``` is the ```query keyword```.
   
   3. The which statement: ```which schema=['schema://username:password@schema.quickcopus.cn/ris/token'], corpus=['cssci'='http://username:password@corpus.quickcopus.cn/sci/token'],license=['license'='http://licence.quickcoprus.cn/token']```
    
    The keyword ```schema``` indicates the schema of the query object. All the query fileds must belongs to the query object.

   The value of schema includes the _schmema protocol_ ```schema://```, _schema server URL_ ```username:password@schema.quickcopus.cn```,  _schema class_ ```ris``` and _schema token_ ```schematoken```. The Token value is commonly a [UUID](https://en.wikipedia.org/wiki/UUID) value.

    The keyword ```corpus``` indicates the source of the corpus servers. The corpus statement includes a serials of [Maps](https://en.wikipedia.org/wiki/Hash_table). The key of map is ```cssci```, and the value of map is ```http://username:password@corpus.quickcopus.cn/sci/token```. 
   

2. Constraint:
   1. In this statement, we can download the data from the corpus server according to the which statment. 
   2. If you run on the web terminal of the www.quickcorpus.cn then you don't need a licence!

## Figure.1 The life cycle of the QQL

![Quickcorps life cycle](images/qqllifecycle.png)

## Figure.2 The abstract syntax of _CQL1.qql_

![The abstract syntax tree of CCL1](images/ccl1_ast.png)

## Description of Figure.1 and Figure.2

The life cycle of the QQL includes five steps:
1. The Tokenizer
2. The Parser
3. The B-Tree module
4. The Pager module
5. The OS Interface 

In the ```step 1``` and ```step 2```, the compiler will parse the abstarct syntax tree in the Figure.2

Before ```step 3``` , the compiler will check the decision table of the corpus as Figure.3

### Figure.3 the decision table of the corpus

1. Validating the license token and corpus token:
   1. Is the license token valided? 
      1. If no, the program will exit and show a error message;
      2. If yes, the program continue executing.
   2. Is the corpus token valided? 
      1. If no, the program will exit and show a error message;
      2. If yes, the program continue executing.
2. Validating the schema.
   1. The schema is a validated [JSON](https://en.wikipedia.org/wiki/JSON) file.
   2. The json file will be downloaded in the ```cache``` folder with the file name ```_class_ _ _token_ .json```, such as `ris_204c837db67e462987595675a78c7eca.json`.
   3. Generate the [Data Transfer Object (DTO)](https://en.wikipedia.org/wiki/Data_transfer_object) according to the json file. The name of the DTO is ```_class_ _ _token_ .class```, such as `Ris204c837db67e462987595675a78c7eca.class`.

3. Validating the cached corpus.

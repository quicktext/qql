# Hello World from QQL!

The Quicktext Query Language includes two parts:
1. The Corpus Query Language (CQL) of the Quicktext Query Language (QQL)
2. The Corpus Control Language (CCL) of the Quicktext Query Language (QQL)

QQL is ___not___ a case-sensitive language.

In this section, I will give some demos for learning the CCL of the QQL.

The demos are written in the Java Language, but you can use any other languages as well.

# DEMO1: The simplest CQL statement
## Filename : _CQL1.qql_
```SQL
select 'title','author','abstract','url' from 'cssci'
where keyword=['doc2vec'] 
which 
	schema=[
		'schema://username:password@schema.quickcopus.cn/ris/token'], 
	corpus=[
		'cssci'='http://username:password@corpus.quickcopus.cn/sci/token'],
	license=[
		'license'='http://licence.quickcoprus.cn/token']
/*If you run on the web terminal of the www.quickcorpus.cn then you don't need a licence!*/;
```

## Figure.1 The abstract syntax of _CQL1.qql_

![The abstract syntax tree of CCL1](images/ccl1_ast.png)

## Description of Figure.1

1. The simplest statement includes three essential statments:
   1. The query statement:  ```select 'title','author','abstract','url' from 'cssci'```

   ```'title','author','abstract','url'``` are called ```query _fileds_```, and ```cssci``` is called ```query _corpus_```.
   
   2. The where statement: ```where keyword=['doc2vec'] ```
   
   ```doc2vec``` is the ```query keyword```.
   
   3. The which statement: ```which schema=['schema://username:password@schema.quickcopus.cn/ris/token'], corpus=['cssci'='http://username:password@corpus.quickcopus.cn/sci/token'],license=['license'='http://licence.quickcoprus.cn/token']```
    
    The keyword ```schema``` indicates the schema of the query object. All the query fileds must belongs to the query object.

    The keyword ```corpus``` indicates the source of the corpus servers. The corpus statement includes a serials of [Maps](https://en.wikipedia.org/wiki/Hash_table). The key of map is ```cssci```, and the value of map is ```http://username:password@corpus.quickcopus.cn/sci/token```. 
    

2. Constraint:
   1. In this statement, we can download the data from the corpus server according to the which statment. 
   2. If you run on the web terminal of the www.quickcorpus.cn then you don't need a licence!

## Figure2. The life cycle of the QQL

![Quickcorps life cycle](images/qqllifecycle.png)

1. The Tokenizer
2. The Parser
3. The B-Tree module
4. The Pager module
5. The OS Interface 



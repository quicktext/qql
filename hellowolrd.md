# Hello World from QQL!

The Quicktext Query Language includes two parts:
1. The Corpus Query Language (CQL) of the Quicktext Query Language (QQL)
2. The Corpus Control Language (CCL) of the Quicktext Query Language (QQL)

In this section, I will give some demos for learning the CCL of the QQL.

The demos are written in the Java Language, but you can use any other languages as well.

## The simplest CCL statement
> Filename : _CCL1.qql_
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

## The abstract syntax of _CCL1.qql_

![The abstract syntax tree of CCL1]<images/ccl1._ast.png>



# The demo scripts of the QQL

## 1. The simplest QQL script
```SQL
select 	'title','author','abstract','url' from	'cssci','cscd'
where keyword=['media','AI','AI+media'],
which 
	schema=[
		'cssci'='http://www.quicktext.cn/ris?eeaeb365bb7a45cbb1f8773d63ead0fc',
		'cscd'='http://www.quicktext.cn/ris?bda02d1d34cd45fc9ce3f1d05e2dde57'], 
	corpus=[
		'cssci'='http://cssci.doi.ai/json?q=',
		'cscd'='http://cscd.doi.ai/json?q='],
	license=[
		'license'='http://www.quickcoprus.cn/debug.qprivate']
```

## 2. The asbtract syntax tree of this QQL

![The asbtract syntax tree of this QQL](../images/simplest.qql.png)


## 3. A complex QQL script
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
	sort = ['year' = asc,'name' = asc],
	filter = ['name' = 'information','year' = 'analytics'],
	black filter = ['name'='data','year'='research']
with 
	plugins=['mail'='genix@quicktext.cn','sms'='+8600000000000']
when 
	cron=['0,0,0,0,0,0,0'],
	daemon=[
		'daemon'='http://username:password@daemon.quickcoprus.cn/cron/token6',
		'daemon'='http://username:password@daemon.quickcoprus.cn/cron/token7',
		'daemon'='http://username:password@daemon.quickcoprus.cn/cron/token8']
which 
	schema=[
		'cssci'='http://www.quicktext.cn/ris?eeaeb365bb7a45cbb1f8773d63ead0fc',
		'cscd'='http://www.quicktext.cn/ris?bda02d1d34cd45fc9ce3f1d05e2dde57'], 
	corpus=[
		'cssci'='http://cssci.doi.ai/json?q=',
		'cscd'='http://cscd.doi.ai/json?q=',
		'patent'='http://username:password@corpus.quickcopus.cn/sci/token3'],
	plugin=[
		'mail'='http://username:password@action.quickcorpus.cn/mail/token4',
		'sms'='http://username:password@action.quickcorpus.cn/sms/token5'],
	model=['tensorflow'='D:/google.model','caffe'='C:/berkery.model'],
	license=[
		'license'='http://www.quickcoprus.cn/debug.qprivate']
```

## 4. The asbtract syntax tree of this QQL

![The asbtract syntax tree of this QQL](../images/complex.qql.png)


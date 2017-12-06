---
title: vue��������mock
---
> ���ǳ�����ǰ�˿�����ʱ����Ҫ�õ����ָ��������ݣ����ʱ�������������뵽�Һ�˵�ͬ�»�ȡ�ӿڡ��������Ŀ��ǰ���ͬʱ����������£�������һЩҳ���ʱ��Ͳ���ͬ���Ļ�õ��ӿ����ݣ����ʱ�����Ǿ���Ҫ�ͺ��ͬ��Э�����ֶΣ���������mock������ҳ��ļ�������

- ������vue�ٷ��ṩ�������й������������ã�

``` bash
û�а�װvue�ٷ������ͯЬ�뵽�����ӳ���װ�� https://cn.vuejs.org/v2/guide/installation.html#NPM
```
- ��ʼ����������Ŀ¼�ṹ

![image](http://i4.bvimg.com/523028/e0434a3c5dbe9a73.png)

- Ȼ���ڸ�Ŀ¼�´���һ���� mock ���ļ��У��ڽ���һ��js�ļ�


``` bash
������ִ��npm ��װ faker �� lodash

npm install faker
npm install lodash
```
- ��mock�ļ����µ�js�ļ���������´�����ܿ��ٵ������û�����,�����APIʹ�ò鿴[faker�ĵ�](https://github.com/FotoVerite/Faker.js)
``` bash
module.exports = function() {
  var faker = require("faker");
  faker.locale = "zh_CN";
  var _ = require("lodash");
  return {
    people: _.times(10, function(n) {
      return {
        id: n,
        name: faker.name.findName(),
        avatar: faker.internet.avatar()
      };
    }),
  };
};

```
- ��config�����������ǵĽӿڴ���

![image](http://i4.bvimg.com/523028/b3300aa76b139e04.png)

- ��package.json�ļ� ���á�scripts�� �������´��� 

``` bash
"mock": "json-server mock/data.js",
"mockdev": "npm run mock | npm run dev"
```
![image](http://i1.bvimg.com/523028/bbb92d57ef9168df.png)
###### ����Ĵ���������vue���������mock���ݵķ���

``` bash
������ִ�� npm run mockdev ��������

��vue�ļ���ʹ��http://localhost:3000/people���Ӿ��ܻ�ȡ������
```

![image](http://i1.bvimg.com/523028/b93e1a237ed83850.png)




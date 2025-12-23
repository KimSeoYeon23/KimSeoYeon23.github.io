---
layout: post
title:  "Sequelize"
date:   2025-12-23 11:45:00 +0900
categories: 
  - Dev
  - node
tag: node
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

> 시퀄라이즈(Sequelize)는 DB 작업을 쉽게 할 수 있도록 도와주는 ORM 라이브러리
> 
> ORM(Object-Relational Mapping)은 자바스크립트 객체와 관계형 데이터베이스를 서로 연결해주는 도구

  

## 설치

`sequelize`와 `sequelize-cli` 그리고 `mysql2`를 설치한다.

```Shell
npm install sequelize sequelize-cli mysql2
```

`sequelize-cli`는 시퀄라이즈 명령어를 실행하기 위한 패키지 라이브러리이다. Global 설치해도 상관 없다.

`mysql2`는 MySQL과 연결해주는 드라이버이다.

설치를 완료 후 `sequelize init` 명령어를 실행한다.

```Shell
sequelize init
```

해당 명령어를 실행하면 아래와 같이 디렉터리 파일이 생성이 된다.

![[99.Atteachment/image 9.png|image 9.png]]

`models/index.js`는 `config/config.json`의 설정 값을 읽어서 시퀄라이즈를 생성한 후 models 디렉토리의 model들을 db 객체에 정의한다.

  

**config/config.json**

```JSON
{
  "development": {
    "username": "root",   // DB와 연결할 유저 "이름"
    "password": null,     // DB와 연결할 유저 "비밀번호" 
    "database": "database_development",   // 사용할 Database 이름
    "host": "127.0.0.1",  // DB 서버 호스트
    "dialect": "mysql"    // DB 타입 설정 (mysql이 아니면 다른 DB 설정)
  },
  "test": {
    "username": "root",
    "password": null,
    "database": "database_test",
    "host": "127.0.0.1",
    "dialect": "mysql"
  },
  "production": {
    "username": "root",
    "password": null,
    "database": "database_production",
    "host": "127.0.0.1",
    "dialect": "mysql"
  }
}
```

**model/index.js**

```JavaScript
'use strict';

const fs = require('fs');
const path = require('path');
const Sequelize = require('sequelize');
const process = require('process');
const basename = path.basename(__filename);
const env = process.env.NODE_ENV || 'development';
const config = require(__dirname + '/../config/config.json')[env];
const db = {};

let sequelize;

// config/config.json 파일에 있는 정보를 가져와 sequelize 객체를 생성한다.
if (config.use_env_variable) {
  sequelize = new Sequelize(process.env[config.use_env_variable], config);
} else {
  sequelize = new Sequelize(config.database, config.username, config.password, config);
}

// 우리가 작성한 Table 파일을 찾아온다.
fs
  .readdirSync(__dirname)
  .filter(file => {
    return (
      file.indexOf('.') !== 0 &&
      file !== basename &&
      file.slice(-3) === '.js' &&
      file.indexOf('.test.js') === -1
    );
  })
  .forEach(file => {
    const model = require(path.join(__dirname, file))(sequelize, Sequelize.DataTypes);
    db[model.name] = model;
  });

// DB에 모델 이름을 연결한다.
Object.keys(db).forEach(modelName => {
  if (db[modelName].associate) {
    db[modelName].associate(db);
  }
});

db.sequelize = sequelize;
db.Sequelize = Sequelize;

module.exports = db;
```

models는 실제로 MySQL과 매핑될 객체들이 정의된다. 객체들을 정의하기 전에 먼저 서버에 모델을 연결 시켜주도록 한다.

**app.js**

```JavaScript
const { sequelize } = require('./models')

var app = express();    // --- 1
sequelize.sync()
```

models > model에 가서 MySQL에 정의한 테이블을 시퀄라이즈에 정의한다. MySQL의 테이블과 컬럼 내용은 시퀄라이즈에 정의하는 내용과 **일치해야 정확하게 대응되므로** MySQL의 내용과 동일하게 작성하도록 한다. 다만 `id` 만은 시퀄라이즈가 알아서 연결하므로 `id`컬럼은 따로 작성해주지 않아도 된다.

  

**user 테이블**

```JavaScript
module.exports = (sequelize, DataTypes) => {
  const User = sequelize.define('user', {
    name: {
      type: DataTypes.STRING(20),
      allowNull: false,
      unique: true
    },
    age: {
      type: DataTypes.INTEGER.UNSIGNED,
      allowNull: false
    },
    comment: {
      type: DataTypes.TEXT,
      allowNull: true
    }
  }, {
    timestamps: true
  })

  return User
}
```

  

**comment 테이블**

```JavaScript
module.exports = (sequelize, DataTypes) => {
  return sequelize.define('comment', {
    comment: {
      type: DataTypes.STRING(100),
      allowNull: false
    }
  }, {
    timestamps: true
  })
}
```

`timestamps` 속성은 `true`면 `createdAt(생성 시간)`과 `updatedAt(수정 시간)`을 자동으로 입력해준다.

  

- 시퀄라이즈 자료형은 MySQL과 조금 다르므로 아래 표를 참고하도록 한다.
    
    |   |   |
    |---|---|
    |Sequelize|MySQL|
    |STRING|VARCHAR|
    |INTEGER|INT|
    |BOOLEAN|TINYINT|
    |DATE|DATETIME|
    

  

이제 model을 생성했으므로 model들을 시퀄라이즈와 연결해주고, 테이블 간의 관계를 정의해 주어야 한다. 관계에는 1:1 관계, 1:N 관계, N:M 관계가 있고 각각의 관계들을 시퀄라이즈는 메서드로 표현한다.

시퀄라이즈에서는 관계를 아래와 같은 메서드들로 정의한다.

**1:N**

- 1 → N: hasMany
- N → 1: belongsTo

  

**1:1**

- 1 → 1: hasOne

  

**N:M**

- N → M: belongsToMany

  

이 중 우리가 예시로 작성하고 있는 user와 comment관계는 1:N 관계이므로 models > index.js에 아래와 같이 작성해줄 수 있다.

```JavaScript
// model을 sequelize에 연결해주는 코드
db.User = require('./user')(sequelize, Sequelize);
db.Comment = require('./comment')(sequelize, Sequelize);


// model들 간의 관계를 정의해주는 코드
db.User.hasMany(db.Comment, { foreignKey: 'commenter', sourceKey: 'id'});
db.Comment.belongsTo(db.User, { foreignKey: 'commenter', sourceKey: 'id'});
```

  

이제 Node 서버를 실행시켜보도록 한다. 서버를 실행시키면 시퀄라이즈가 스스로 SQL문을 실행시켜주는데, 자세히 읽어보면 **IF NOT EXISTS**라고 되어 있는데, 만약 위에서 정의한 테이블들이 존재하지 않을 시에는 자동적으로 위의 테이블들을 생성해주게 된다.

![](https://i.imgur.com/v1xvAYQ.png)

  

## Sequelize query

시퀄라이즈는 객체와 데이터베이스 사이에서 서로를 매핑해주는 역할을 한다.

SQL문을 자바스크립트로 생성하는 형태이기 때문에 시퀄라이즈만의 방법을 따라야 한다. 시퀄라이즈 쿼리는 프로미스를 반환하기 때문에 `then`을 붙여 결괏값을 받을 수 있다 .프로미스 형태이기 때문에 `async/await` 문법 역시 함께 사용할 수 있다.

### create, select

```JavaScript
const { User } = require('../models');


// create
User.create({
  name: 'ooeunz',
  age: '25',
  comment: '안녕하세요'
});


// select
User.findOne({});

User.findAll({});


// select column
User.findAll({
  attributes: ['name', 'comment']
});
```

처음 시퀄라이즈 문법을 접하게 되면 조금 당황할 수 있다. 앞서 이야기했듯 시퀄라이즈는 객체와 데이터베이스 사이에서 매핑해준다. 때문에 해당 코드를 작성하면 시퀄라이즈가 알아서 데이터베이스에 매핑해준다.

위의 코드를 살펴보면 `require('../models);`라는 코드를 유의할 필요가 있다. 정확히 말하면 models의 index.js를 require하는 코드이지만 해당 디렉토리를 require하면 index.js로 자동으로 경로가 설정되기 때문에 index.js는 생략할 수 있다. 즉 models/index.js에 정의했던 User를 불러오는 코드이다. 이후의 코드 중에 살펴볼만한 것은 `findAll`에 attributes이다. `attributes`는 원하는 전체를 불러오는 코드가 아닌 특정 컬럼만 불러오고 싶을 때 이용한다. 위의 코드를 쿼리로 살펴본다면,

`SELECT name, comment FROM database.table;`

과 같은 형태가 될 것이다.

  

### 쿼리 수행 조건

```JavaScript
const { User, Sequelize: { Op } } = require('../models');

// 초과
User.findAll({
  attributes: ['name', 'comment'],
  where: {
    age: { [Op.gt]: 30 }
  }
})

// or
User.findAll({
  attributes: ['name', 'comment'],
  where: {
    [Op.or]: [{ age: {[Op.gt]: 25} }, { name: 홍길동 }]
  }
})

// order & limit
User.findAll({
  attributes: ['name', 'comment'],
  order: [['age', 'DESC']],
  limit: 1
})
```

이번에는 models에서 `Sequelize: {Op}` 객체를 함께 받아왔다. `Op`객체에는 여러가지 활용 가능한 연산자들이 포함되어 있다.

- Op.gt(초과)
- Op.gte(이상)
- Op.lt(미만)
- Op.lte(이하)
- Op.ne(같지 않음)
- Op.or(또는)
- Op.in(배열 요소 중 하나)
- Op.notIn(배열 요소와 모두 다름)

추가적으로 order와 limit과 같은 쿼리 역시 수행할 수 있다.

  

### 수정, 삭제

```JavaScript
// update
User.update({
  comment: '수정 내용'
}, {
  where: { id: 1}
});


// delete
User.destory({
  where: { id: 1}
});
```

  

> 출처: [https://ooeunz.tistory.com/71](https://ooeunz.tistory.com/71)
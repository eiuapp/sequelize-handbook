---
title: belongsTo
weight: 2
bookToc: false
---

## targetKey

```
var User = this.sequelize.define('user', {/* attributes */})
  , Company  = this.sequelize.define('company', {/* attributes */});

User.belongsTo(Company, {foreignKey: 'fk_companyname', targetKey: 'name'}); // 为User 添加 fk_companyname 目标键
```

表示

User 表的 fk_companyname = Company 表的 name，

这个时候，company 表的 主键，不一定是 name, 可以是其它的列
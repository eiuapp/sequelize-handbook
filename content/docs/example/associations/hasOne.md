---
title: hasOne
weight: 3
bookToc: false
---

## foreignKey

- hasOne 或者 hasMany 的 foreignKey 都是 目标模型
- belongsTo 或者 belongsToMany 的 foreignKey 都是 源模型
```
Project.hasOne(User, { foreignKey: 'initiator_id' })
```

这个定义 的意思是：

Project.Id = User表中的 外键 initiator_id 的值, 而不是 User 表中的 project_id

## 如果想对一个表做两次连接查询

```
Team.hasOne(Game, {as: 'HomeTeam', foreignKey : 'homeTeamId'});
Team.hasOne(Game, {as: 'AwayTeam', foreignKey : 'awayTeamId'});
```

是指 

1.   Game 中的 homeTeamId 值  =  Team 表中的 id   
的 同时：
2.  Game 中的 awayTeamId 值  =  Team 表中的 id  

转化成 sql ，则是：

```
select * from Team inner join Game AS  HomeTeam on HomeTeam.homeTeamId=Team.id inner join Game As AwayTeam on AwayTeam.awayTeamId = Team.id
```


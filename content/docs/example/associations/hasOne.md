---
title: hasOne
weight: 2
bookToc: false
---

## foreignKey

```
Project.hasOne(User, { foreignKey: 'initiator_id' })
```

这个定义 的意思是：

User表中的 外键 initiator_id 的值  =  Project.Id

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


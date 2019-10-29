
## associate 使用 

```
User.associate = function(models) {
  User.belongsTo(models.Company, {foreignKey: 'companyId', as: 'company'})
};
```

出自于：

- https://medium.com/@eth3rnit3/sequelize-relationships-ultimate-guide-f26801a75554
- https://github.com/1134506391/egg-rbac 
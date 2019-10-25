---
title: scope
weight: 4
bookToc: false
---

https://itbilu.com/nodejs/npm/41qaV3czb.html#associations-scopes

## hasMany scope

```
this.Image.hasMany(this.Comment, {
  foreignKey: 'commentable_id',
  constraints: false,
  scope: {
    commentable: 'image'
  }
});
```

表示

Image.id = comment.commentable_id 而且 comment.commentable = 'image';

```
this.Comment.belongsTo(this.Image, {
  foreignKey: 'commentable_id',
  constraints: false,
  as: 'image'
});
```

就表示 

comment.commentable_id = image.id 

## ItemTag

ItemTag = sequelize.define('item_tag', {
  tag_id: {
    type: DataTypes.INTEGER,
    unique: 'item_tag_taggable'
  },
  taggable: {
    type: DataTypes.STRING,
    unique: 'item_tag_taggable'
  },
  taggable_id: {
    type: DataTypes.INTEGER,
    unique: 'item_tag_taggable',
    references: null
  }
});

Post.belongsToMany(Tag, {
  through: {
    model: ItemTag,
    unique: false,
    scope: {
      taggable: 'post'
    }
  },
  foreignKey: 'taggable_id',
  constraints: false
});

Tag.belongsToMany(Post, {
  through: {
    model: ItemTag,
    unique: false
  },
  foreignKey: 'tag_id'
});
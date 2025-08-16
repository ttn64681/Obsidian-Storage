***When to use?*** -> Inside Operation Function Parameters:
- w/in update queries
```
// Update a post's title and add a comment
await Post.findByIdAndUpdate('60d21b4667d0d85', {
  $set: { title: 'New Title' },
  $push: { comments: { user: '60d21b4667d0d86', comment: 'Great post!' } },
});
```
- w/in aggregation pipelines
```
  await Post.aggregate([
    { $match: { _id: '60d21b4667d0d85' } },
    { $set: { title: 'New Title' } },
  ]);
```
- w/in bulk operations
```
  await Post.bulkWrite([
    { updateOne: { filter: { _id: '60d21b4667d0d85' }, update: { $set: { title: 'New Title' } } } },
  ]);
```

<hr>

DEFINITIONS

1. $set
- sets the value of a field
- for updating a single field
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $set: { title: 'New Title' } });
```

2. $push
- adds an element to an array
- i.e., adding a comment to a post's comments array
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $push: { comments: { user: '60d21b4667d0d86', comment: 'Great post!' } } });
```

3. $pull
- removes an elements from an array
- i.e., removing a like form a post's likes array
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $pull: { likes: '60d21b4667d0d86' } });
```

4. $addToSet
- adds an element to an array if it doesn't already exist
- i.e., adding a like to a post's likes array (avoiding duplicates)
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $addToSet: { likes: '60d21b4667d0d86' } });
```

5. $inc
- increments a numeric field
- i.e., incrementing a view count
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $inc: { views: 1 } });
```

6. $unset
- removes a field from a doc
- i.e., removing an optional field
```
await Post.findByIdAndUpdate('60d21b4667d0d85', { $unset: { description: 1 } });
// the '1' doesn't matter in this case, it's just convention, a placeholder
// you could put true, false, "anything"
```


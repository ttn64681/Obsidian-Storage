**Document:** (rows)
- Single record in MongoDB, stored as a JSON-like object (BSON - binary json)
```
{
	"_id": "",
	"courseId": "CSCI-1301",
	"resourceUrls": [
		{
			"url": "...com"
			"description": "description"
		}
	],
	"posts": [""],
}
```

**Collection:** (columns)
- Group of documents, similar to table in relational database
```
  // Collection: "courses"
  [
    {
      "_id": "60d21b4667d0d8992e610c85",
      "courseId": "CSCI-1301",
      "title": "Introduction to Computer Science",
      ...
    },
    {
      "_id": "60d21b4667d0d8992e610c86",
      "courseId": "CSCI-1302",
      "title": "Data Structures",
      ...
    },
    ...
  ]
```

**Database:**
- A container for collections
```
Database: "coursehub"
  ├── Collection: "courses"
  │   ├── Document: { courseId: "CSCI-1301", title: "Intro to Comp Sci", ... }
  │   ├── Document: { courseId: "CSCI-1302", title: "Data Structures", ... }
  │   └── ...
  ├── Collection: "posts"
  │   ├── Document: { title: "Tips", url: "https://youtube.com/...", ... }
  │   ├── Document: { title: "Programming", url: "https://youtube.com/...", ... }
  │   └── ...
  ├── Collection: "users"
  │   ├── Document: { username: "john_doe", email: "john@example.com", ... }
  │   ├── Document: { username: "jane_doe", email: "jane@example.com", ... }
  │   └── ...
  └── Collection: "comments"
      ├── Document: { postId: "#", user: "john", comment: "Great!", ... }
      ├── Document: { postId: "#", user: "jane", comment: "Thanks!", ... }
      └── ...
```

<hr>

COMMANDS:

1. create()
- creates new doc in collection
- params: an object containing doc data
```
const newCourse = await Course.create({
	courseId: '...',
	prefix: 'CSCI',
	number: '1301',
})
```

2. find()
- retrieves multiple documents matching a query
- query object (optional) and options (like sorting, limiting, etc.)
```
const courses = await Course.find({ prefix: 'CSCI' }).sort({ number: 1 })
```

3. findOne()
- retrieves single doc matching a query
- query object
```  
const course = await Course.findOne({ courseId: 'CSCI-1301' });
```

4. findById()
- retrieves doc by its \_id
- params: the doc's \_id (as string or ObjectId)
```
const course = await Course.findById('60d21b4667d0d8992e610c85');
```

5. findByIdAndUpdate()
- updates doc by its \_id and returns updated doc
- params: the doc's \_id, and update object, and options (like {new: true} to return updated doc).
```
  const updatedCourse = await Course.findByIdAndUpdate(
    '60d21b4667d0d8992e610c85',
    { title: 'Advanced Computer Science' },
    { new: true }
  );
```

6. findByIdAndDelete()
- deletes a doc by its \_id and returns deleted doc
- params: the doc's \_id
```
  const deletedCourse = await Course.findByIdAndDelete('...');
```

7. updateOne()
- updates single doc that matches a query
- params: a query object, an update object, and options
```
  await Course.updateOne(
    { courseId: 'CSCI-1301' },
    { $set: { title: 'Introduction to Programming' } }
  );
```

8. updateMany()
- updates multiple docs that match a query
- params: a query object, an update object, and options
```
  await Course.updateMany(
    { prefix: 'CSCI' },
    { $set: { department: 'Computer Science' } }
  );
```

9. deleteOne()
- deletes a single doc that matches a query
- params: a query object
```
  await Course.updateMany(
    { prefix: 'CSCI' },
    { $set: { department: 'Computer Science' } }
  );
```

10. populate()
- replaces specified fields in a doc w/ documents from another collection 
	- (used for replacing references w/ the actual documents)
	- uses the ref property in the schema to know which collection to look in...
- you can chain populate calls to populate multiple fields
	- you can also chain populate calls to populate a nested field
```
const post = await Post.findById('60d21b4667d0d85');
console.log(post); // { _id: '60d21b4667d0d85', title: 'Sick Coding Tips', user: '60d21b4667d0d86', ... }

const post = await Post.findById('60d21b4667d0d85').populate('user', 'username');
console.log(post); // { _id: '60d21b4667d0d85', title: 'Sick Coding Tips', user: { _id: '60d21b4667d0d86', username: 'john_doe' }, ... }

  // Fetching posts to display in the UI (read-only)
  const posts = await Post.find({ course: course._id })
    .populate('user', 'username')
    .populate('course')
    .populate('comments.user', 'username') // populate comments.user
    .sort({ likes: -1, createdAt: -1 })
    .lean();
```

11. lean()
- returns plain JS object instead of a Mongoose doc 
	- Use lean() for read-only operations to get better performance.
	- Don't use lean() if you need Mongoose methods (like save()).
- params: none
```
  // Fetching posts to display in the UI (read-only)
  const posts = await Post.find({ course: course._id })
    .populate('user', 'username')
    .populate('course')
    .populate('comments.user', 'username')
    .sort({ likes: -1, createdAt: -1 })
    .lean();
```

12. sort()
- sorts the result of a query, returning nothing
- params: a sorting object (e.g., { field: 1 } for ascending, -1 for descending)
```
const courses = await Course.find().sort({ prefix: 1, number: 1 });
```


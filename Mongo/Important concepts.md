- All mongoose operations return promises
	- ***this means you should use await on them***

Likes and Comments:
- Use MongoDB's update operators w/ corresponding API routes to add or remove likes/comments:
	- $push
	- $pull
- identify the specific place where you are adding/removing these using the container id


Fetching Something IN ORDER:
- $match
	- find something given a specific key
getting in order:
- $unwind
	- deconstruct the posts array to treat each item as a separate document
- $sort
	- sort the order you fetch the items by specific condition (e.g. length of the likes array in descending order [post1likes: "23", post2likes: "17", ...])
- $group
	- group sorted posts back under original course doc


Finding something w/in DB:
- findOne()
	- retrieves document given a query
	- query ex:
		- { courseKey: 'CS1301' }
		- will look for a document with that specific query key

Adding to a specific collection in DB:
- updateOne()
	- updates a document
	- then use $push
		- add to a specific object key or array of that document

Liking Post



```
import { NextApiRequest, NextApiResponse } from 'next';
import { fetchCoursePosts, addPost } from '@/dbInterface/dbOperations';

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  const { courseId } = req.query;

  switch (req.method) {
    case 'GET':
      const fetchResult = await fetchCoursePosts(courseId as string);
      if (!fetchResult.success) {
        return res.status(404).json({ error: fetchResult.error });
      }
      return res.status(200).json(fetchResult.posts);

    case 'POST':
      const addResult = await addPost({
        ...req.body,
        courseId: courseId as string,
      });
      if (!addResult.success) {
        return res.status(400).json({ error: addResult.error });
      }
      return res.status(201).json(addResult.post);

    default:
      res.setHeader('Allow', ['GET', 'POST']);
      res.status(405).end(`Method ${req.method} Not Allowed`);
  }
}

// Example frontend fetch requests:

// Using courseId string
const responseGetCourse = await fetch(`/api/courses/CSCI-1301`);

// For nested routes (fetching posts for a course)
const responseGetPostsForCourse = await fetch(`/api/courses/CSCI-1301/posts`);

// For liking a post (assuming you have a /api/posts/[postId]/like endpoint)
const responseLikePost = await fetch(`/api/posts/507f1f77bcf86cd799439011/like`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ userId: 'user123' }),
});
```
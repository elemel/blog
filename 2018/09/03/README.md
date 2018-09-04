# Blending face normals and vertex normals

During the last few days,
I have tried to improve the look of the Dual Contouring output by applying the normals from the distance field.
The previous screenshots all displayed normals recalculated by Unity.
These were always face normals because the algorithm generated separate vertices for each triangle.
For a smoother look,
we could either share vertices between triangles or supply explicit normals.
The former alternative seemed unattractive, given that we do want sharp edges and corners in some cases.
Proceeding with the latter alternative,
I calculated face normals from the cross product of the triangle edges.
Some of the smaller triangles ended up black.
Could this be related to floating-point precision?
Not this time, but stay tuned for that topic in future posts.
The problem was rather that Unity normalizes small vectors to zero.
Let's not normalize that kind of behavior.

Now wielding artisanal, non-zero face normals as well as vertex normals from the distance field, I carried on with my experiments. In the end, I settled for

- the vertex normal when it's within 15 degrees of the face normal,
- the face normal when the difference is above 30 degrees,
- and a smoothstepped blend of both in between.

Speaking of smoothstepping,
Unity's smoothstep function doesn't do what I assumed.
That was easy to fix once I understood what the problem was.
At this point, the algorithm finally yielded a mesh with both smooth and sharp features.
There are visual artifacts of facets and cuts where more sampling is required.
And that's the price we pay.

![Blending face normals and vertex normals](smooth.png)

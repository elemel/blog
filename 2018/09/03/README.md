# Blending face normals and vertex normals

During the last few days,
I have tried to improve the look of the Dual Contouring output by applying the normals from the distance field.
The previous images all displayed normals recalculated by Unity.
These were face normals since the algorithm generated separate vertices for each triangle.
For a smoother look,
we could either share vertices between triangles or supply explicit normals.
The former alternative seemed unrealistic,
since we actually do want sharp edges and corners in some cases.
I started by calculating my own face normals from the cross product of the triangle edges.
But some of the smaller triangles ended up black.
Could this be related to floating-point precision?
Not this time, but we will most likely run into that later.
The problem here was that Unity's vector class normalizes small vectors to zero.
That kind of behaviour should never be normalized.

Now wielding artisanal, non-zero face normals as well as vertex normals from the distance field, I carried on with my experiments. In the end, I settled for

- the vertex normal when it's within 15 degrees of the face normal,
- the face normal when the difference is above 30 degrees,
- and a smooth blend of both in between.

Another problem that surfaced during experimentation was that Unity's smoothstep function doesn't do what I was hoping for.
I was already starting to sense a pattern of unreasonable expectations from my side.
Luckily, these things can be sorted out quickly once identified.
The algorithm finally yielded a mesh with both smooth and sharp features.
There are visual artifacts of facets and cuts where more sampling is required.
And that's the price we pay.

![Blending face normals and vertex normals](smooth.png)

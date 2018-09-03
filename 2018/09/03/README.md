# Blending face and vertex normals

During the last few days,
I have experimented with sampled mesh normals from the distance field.
The previous images all used normals recalculated by Unity.
Since my Dual Contouring implementation generates separate vertices for each triangle,
the recalculated normals would be face normals.
When I started providing normals myself,
some of the smaller triangles ended up black.
The problem turned out to be that Unity's vector class unexpectedly truncates small vectors to zero when normalizing.
That kind of behaviour should never be normalized.

Now wielding artisanal, non-zero normals, I carried on with my experiments. In the end, I settled for

- the vertex normal from the distance field when it's within 15 degrees of the triangle's face normal,
- the face normal when the difference is above 30 degrees,
- and a smooth blend of both in between.

Another problem that cropped up here was that Unity's smoothstep function doesn't do quite what I expected.
Once that was sorted out by adapting some code from Wikipedia,
the approach yielded output meshes with both smooth and sharp features.
A visual artifact of the thresholds is that undersampled features look faceted.
And that's the price we pay.

![Blending face and vertex normals](smooth.png)

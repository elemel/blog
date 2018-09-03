# Blending face and vertex normals

During the last few days,
I have experimented with using normals sampled from the distance field for the output mesh.
The previous images all used normals recalculated by Unity.
Since my Dual Contouring implementation generates separate vertices for each triangle,
the recalculated normals would be face normals.
When I started providing normals myself,
some of the smaller triangles ended up black.
The problem turned out to be that Unity's vector class unexpectedly truncates small vectors to zero when normalizing.
That kind of behaviour should never be normalized.

After some further experimentation with my now artisanal, mostly non-zero normals,
I ended up using

- the vertex normal from the distance field when it's within 15 degrees of the triangle's face normal,
- the face normal when the difference is above 30 degrees,
- and a smooth blend of both in between.

Another problem that I ran into here was that Unity's smoothstep function didn't do quite what I expected.
So I copy-pasted the one from Wikipedia.
Once that was sorted out, the approach yielded output meshes with both smooth and sharp features.
A visual artifact of the thresholds is that undersampled features look faceted.
And that's the price we pay.

![Blending face and vertex normals](smooth.png)

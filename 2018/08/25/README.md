# Terrain chunks with gaps

Behold a small, green planet with a tall, white building in the Unity game engine. I have defined the terrain of the planet as a signed distance field, and have implemented the Dual Contouring algorithm to generate mesh geometry for rendering. In order to support world-scale levels, the terrain is divided into an octree of chunks. The next step will be to stitch together the chunks at the seams, filling those ugly gaps. After that I want to start subdividing and reuniting chunks in the octree based on viewing distance.

![Terrain chunks with gaps](unseamly.png)

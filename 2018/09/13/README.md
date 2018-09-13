# The olive out of space

![The olive out of space](olive.png)

During the last week or so,
I've learned one or two things about compute shaders.
Porting the Dual Contouring code to HLSL improved performance by orders of magnitude.

Unity doesn't have perfect support for compute shaders on Mac.
The most annoying thing is that compilation errors aren't surfaced in the editor.
Instead you can find them on disk here:

```<project>/Library/shadercompiler-UnityShaderCompiler*.log```

The logs aren't cleared between compilations either,
which means that new error messages can easily be lost among the great old ones.
Another, also most annoying thing was that for-loops were incredibly slow to compile under Metal in Mac OS Sierra,
and in many cases failed to compile at all.
The editor hangs during shader compilation,
making the long compilation times even more disturbing.
Thankfully, the compute shader support is a lot better under Metal 2 in High Sierra.

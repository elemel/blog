# The olive out of space

During the last week or so,
I've learned one or two things about compute shaders.
Porting the Dual Contouring code to HLSL improved performance by orders of magnitude.

Unity doesn't have perfect support for compute shaders on Mac.
The most annoying thing is that compile errors aren't surfaced in the editor.
Instead you can find them on disk here:

```<project>/Library/shadercompiler-UnityShaderCompiler*.log```

The error log isn't cleared between shader compilations either.
Another annoying thing is that shader compilation hangs the editor.
The last annoying thing was that for-loops were very slow to compile under Metal in Mac OS Sierra,
and in many situations failed to compile at all.
The compute shader support is a lot better under Metal 2 in High Sierra.

![The olive out of space](olive.png)

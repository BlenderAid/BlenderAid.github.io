---
Title: Render multiple frame ranges at the same time
Date: 2015-03-06 10:56
Taxonomy:
    Category: [Rendering]
    Tag: [Settings, Camera, Frame]
---
Use **[this addon](http://blenderartists.org/forum/showthread.php?281647-Setting-up-batch-render-tasks-%28multiple-sequential-renders)** or the manual method below:

- Go to the text-editor (Shift + F11)
- Make a new text datablock (Ctrl + N)
- Copy&paste the following code into it (Ctrl + C, Ctrl + V)

    import bpy
    sce = bpy.context.scene
    sce.frame_start = 0
    sce.frame_end = 10
    bpy.ops.render.render(animation=True)
    sce.frame_start = 20
    sce.frame_end = 30
    bpy.ops.render.render(animation=True)

- Modify the frame ranges as you like, or add new ones
- Hit the 'Run Script' button (or press Alt + P)

Note that the rendering starts immediately and you probably can’t see the progress. However, you can see the images being saved into the render output folder.

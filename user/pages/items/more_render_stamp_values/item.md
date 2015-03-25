---
title: More render stamp values
date: 2015-03-24 22:54
taxonomy:
    category: [Rendering]
    tag: [Settings, Stamp]
---
Make a text datablock called *stamp_init.py*:

    import bpy

    def stamp_set(scene):
       scene.render.stamp_note_text = \
           "Samples: {samples}  |  Aperture: {aperture:.4f}  |  Blender {ver}  |  Resolution: {reso_x:.0f} x {reso_y:.0f}  |  
           ANIM: Jack  |  COMP: John".format(
           samples=scene.cycles.samples,
           aperture=scene.camera.data.cycles.aperture_size,
           ver=bpy.app.version_string,
           reso_x=scene.render.resolution_x*scene.render.resolution_percentage/100,
           reso_y=scene.render.resolution_y*scene.render.resolution_percentage/100,
           )

    bpy.app.handlers.render_pre.append(stamp_set)

- Click **Register** to run it on .blend startup (good for render farms)
- Enable **Note** in the Render Stamp settings
- **Run** the script once to make test renders with the new stamp values

You can add more values by checking out the python code from different tooltips.

This tip was found from the [Blender Stack Exchange](http://blender.stackexchange.com/questions/26643/how-to-show-render-stamp-for-arbitrary-values/26644#26644)

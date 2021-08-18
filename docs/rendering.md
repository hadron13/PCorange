# Rendering (cgraphics.h, rendering/renderer.h, rendering/sky.h)
## Rendering functions


# **types**:
* ### **render_object** - object rendering data
* ### **renderer** - renderer data
* ### **sky** - sky render data

# **enumerations**:
* RENDERER_MAX_LIGHTS
* RENDERER_MAX_DYN_LIGHTS
* RO_TYPE_AXIS
* RO_TYPE_STATIC
* RO_TYPE_INSTANCE
* RO_TYPE_ANIMATED
* RO_TYPE_PARTICLES
* RO_TYPE_LIGHT
* RO_TYPE_LANDSCAPE
* RO_TYPE_PAINT
* RO_TYPE_SPHERE
* RO_TYPE_ELLIPSOID
* RO_TYPE_CMESH
* RO_TYPE_FRUSTUM
* RO_TYPE_PLANE
* RO_TYPE_LINE
* RO_TYPE_POINT

# **constants**:
* float TIME_SUNRISE  = 0.00;
* float TIME_MORNING  = 0.10;
* float TIME_MIDDAY   = 0.25;
* float TIME_EVENING  = 0.40;
* float TIME_SUNSET   = 0.50;
* float TIME_MIDNIGHT = 0.75;

# **functions**:
## categories:
### **graphics**:
* **void graphics_init()** - initialize graphics
* **void graphics_finish()** - finishe graphics

* **void graphics_set_vsync(bool vsync)** - enable/disable vsync
* **void graphics_set_multisamples(int samples)** - set multisampling sample number
* **void graphics_set_fullscreen(bool fullscreen)** - enable/disable fullscreen
* **void graphics_set_antialiasing(int quality)** - set anti-aliasing quality
* **SDL_GLContext\* graphics_context_new()** - create new OpenGL context
* **void graphics_context_delete(SDL_GLContext\* context)** - delete OpenGL context
* **void graphics_context_current(SDL_GLContext\* context)** - set current OpenGL context
* **int graphics_get_multisamples()** - get multisampling sample number
* **bool graphics_get_fullscreen()** - get fullscreen enabled or disabled
* **int graphics_get_antialiasing()** - get antialiasing qualtity
* **void graphics_viewport_set_title(const char\* title)** - set viewport title
* **void graphics_viewport_set_icon(fpath icon)** - set viewport icon
* **void graphics_viewport_set_position(int x, int y)** - set viewport position
* **void graphics_viewport_set_size(int w, int h)** - set viewport size
* **void graphics_viewport_screenshot()** - take screenshot from viewport
* **const char\* graphics_viewport_title()** - get viewport title
* **int graphics_viewport_height()** - get viewport height
* **int graphics_viewport_width()** - get viewport width
* **float graphics_viewport_ratio()** - get viewport ratio
* **void graphics_set_cursor_hidden(bool hidden)** - hide/show cursor 
* **bool graphics_get_cursor_hidden()** - get cursor shown or hidden
* **void graphics_swap()** - swap buffers
### **rendering**:

* **render_object render_object_static(static_object\* s)** - get render object from static object

* **render_object render_object_instance(instance_object\* s)** - get render object from instance object
* **render_object render_object_animated(animated_object\* a)** - get render object from animated object
* **render_object render_object_particles(particles\* p)** - get render object from particles
* **render_object render_object_light(light\* l)** - get render object from light
* **render_object render_object_axis(mat4 a)** - get render object from axis
* **render_object render_object_sphere(sphere s)** - get render object from sphere
* **render_object render_object_ellipsoid(ellipsoid e)** - get render object from ellipsoid
* **render_object render_object_frustum(frustum f)** - get render object from frustrum
* **render_object render_object_plane(plane p)** - get render object from plane
* **render_object render_object_cmesh(cmesh\* cm, mat4 world)** - get render object from cmesh
* **render_object render_object_landscape(landscape\* l)** - get render object from landscape
* **render_object render_object_paint(mat4 paint_axis, float paint_radius)** - get render object from paint
* **render_object render_object_line(vec3 start, vec3 end, vec3 color, float thickness)** - get render object from line
* **render_object render_object_point(vec3 pos, vec3 color, float size)** - get render object from point

* **renderer\* renderer_new(asset_hndl options)** - create new renderer
* **void renderer_delete(renderer\* dr)** - delete renderer

* **void renderer_set_camera(renderer\* dr, camera\* cam)** - set camera
* **void renderer_set_color_correction(renderer\* dr, asset_hndl t)** - set color correction
* **void renderer_set_vignetting(renderer\* dr, asset_hndl v)** - set vignetting
* **void renderer_set_glitch(renderer\* dr, float glitch)** - set glitch
* **void renderer_set_skydome_enabled(renderer\* dr, bool enabled)** - enable/disable sky dome
* **void renderer_set_sea_enabled(renderer\* dr, bool enabled)** - enable/disable sea
* **void renderer_set_tod(renderer\* dr, float tod, int seed)** - enable/disable tod

* **void renderer_add(renderer\* dr, render_object ro)** - add render object to renderer
* **void renderer_add_dyn_light(renderer\* dr, light\* l)** - add dynamic lightning to renderer

* **void renderer_render(renderer\* dr)** - render with renderer

### **sky**:
* **sky\* sky_new()** - create new sky
* **void sky_delete(sky\* s)** - delete sky
* **void sky_update(sky\* s, float t, uint32_t seed)** - update sky



# Cengine (cengine.h)

## Common functions and structs used across the game engine.

### This is the main component of corange and can be considered a universal include across all files.
### It contains various utilities as well as vector, matrix and geometry maths.

#
# **types**:
* **fpath**     - filesystem path used for opening/saving files
* **timer**     - used for timing
* **type_id**
* **vec2**      - two parameter vector used for math
* **vec3**      - three parameter vector used for math
* **vec4**      - four parameter vector used for math
* **quat**      - quaternion used for rotations
* **quat_dual** - dual quaternion used for rotations
* **mat2**      - 2x2 matrix used for math 
* **mat3**      - 3x3 matrix used for math
* **mat4**      - 4x4 matrix used for math 
* **plane**     - 3D plane
* **box**       - 3D box primitive
* **frustrum**  - 3D frustrum
* **sphere**    - 3D sphere primitive
* **ellipsoid** - 3D ellipsoid primitive
* **capsule**   - 3D capsule primitive
* **vertex**    - 3D mesh vertex
* **mesh**      - 3D mesh
* **model**     - 3D model
#

# **functions**:
## categories:
### **filesystem**:
* **fpath P(const char\* path)** - transforms char* into fpath
* **fpath fpath_full(fpath path)** - get full path
* **fpath fpath_file(fpath path)** - get file name
* **fpath fpath_file_location(fpath path)** - get file location
* **fpath fpath_file_extension(fpath path)** - get file extension

### **errors & debugging**:
* **void at_debug/warning/error(void(\*func)(const char\*))** - register callback for debug/warning/error
* **void debug/warning/error_(const char\*)** - call registered callbacks
* **debug/warning/error(MSG, ...)** - log debug/warning/error
* **alloc_check(PTR)** - checks allocation success
* **SDL_GL_CheckError()** - checks OpenGL error if not in release mode
* **SDL_GL_CheckFrameBuffer()** - checks OpenGL frame buffer status if not in release mode
* **likely(x)** - condtional hinting
* **unlikely(x)** - condtional hinting

### **timing**:
* **timer timer_start(int id, const char\* tag)** - start timer
* **timer timer_split(timer t, const char\* tag)** - split timer
* **timer timer_stop(timer t, const char\* tag)** - stop timer
* **void timestamp(char\* out);** - prints timestamp on **out**

### **framerate**:

* **void frame_begin()** - begin frame
* **void frame_end()** - end frame
* **void frame_end_at_rate(double fps)** - timing for frame end
* **double frame_rate()** - get frame rate
* **double frame_time()** - get frame time
* **char\* frame_rate_string()** - get frame rate as string

### **types**:
* **typeid(TYPE)** - get type_id from type (without size)
* **type_id type_find(char\* type, size_t size)** - get type_id from type name
* **char* type_id_name(int id)**

### **floating point maths**:
* **float max(float x, float y)** - maximum between x and y
* **float min(float x, float y)** - minimum between x and y
* **float clamp(float x, float bottom, float top)** - clamp x
* **float saturate(float x)** - saturate x
* **bool between(float x, float bottom, float top)** - if x is between bottom and top
* **bool between_or(float x, float bottom, float top)** if x is between or is botton or top
* **float lerp(float p1, float p2, float amount)** - interpolation
* **float smoothstep(float p1, float p2, float amount)** - smooth steps interpolation
* **float smootherstep(float p1, float p2, float amount)** - smoother steps interpolation
* **float cosine_interp(float p1, float p2, float amount)** - cosine interpolation
* **float cubic_interp(float p1, float p2, float p3, float p4, float amount)** - cubic interpolation
* **float nearest_interp(float p1, float p2, float amount)** - nearest interpolation
* **float binearest_interp(float tl, float tr, float bl, float br, float x_amount, float y_amount)** - binearest interpolation
* **float bilinear_interp(float tl, float tr, float bl, float br, float x_amount, float y_amount)** - bilinear interpolation
* **float bicosine_interp(float tl, float tr, float bl, float br, float x_amount, float y_amount)** - bicosine interpolation
* **float bismoothstep_interp(float tl, float tr, float bl, float br, float x_amount, float y_amount)** - bismooth step interpolation
* **float bismootherstep_interp(float tl, float tr, float bl, float br, float x_amount, float y_amount)** - bismoother step interpolation

### **vector maths**:
### note: vecn stands for any vector size 2-4, vecn/n stands for two possible sizes

* **vecn vecn_new(float x, float y,...)** crea
* **vecn vecn_zero()** - creates vector with 0
* **vecn vecn_one()** - creates vector with 1
* **vec3 vec3_up()** - creates vector pointing upwards

* **vec3 vec3/4_red()** - creates vector with red color on RGB 
* **vec3 vec3/4_green()** - creates vector with green color on RGB
* **vec3 vec3/4_blue()** - creates vector with blue color on RGB
* **vec3 vec3/4_white()** - creates vector with white color on RGB
* **vec3 vec3/4_black()** - creates vector with black color on RGB
* **vec3 vec3/4_grey()** - creates vector with grey color on RGB
* **vec3 vec3/4_light_grey()** - creates vector with light grey color on RGB
* **vec3 vec3/4_dark_grey()** - creates vector with dark grey color on RGB


* **vecn vecn_add(vecn v1, vecn v2)** - adds two vectors
* **vecn vecn_sub(vecn v1, vecn v2)** - subtracts two vectors
* **vecn vecn_mul(vecn v, float fac)** - multiplies vector with scalar
* **vecn vecn_mul_vecn(vecn v1, vecn v2)** - multiplies two vectors
* **vecn vecn_div(vecn v, float fac)** - divide vector with scalar
* **vecn vecn_div_vecn(vecn v1, vecn v2)** - divide two vectors
* **vecn vecn_pow(vecn v, float exp)** - power vector 
* **vecn vecn_neg(vecn v)** - negative vector
* **vecn vecn_abs(vecn v)** - absolute vector
* **vecn vecn_floor(vecn v)** - truncate vector floating point
* **vecn vecn_fmod(vecn v, float val)** - modulus vector with scalar

* **vecn vec2_max(vec2 v, float x)** - maximum between vector and scalar
* **vecn vec2_min(vec2 v, float x)** - minimum between vector and scalar
* **vecn vec2_clamp(vec2 v, float b, float t)** - clamp vector with scalar

* **bool vecn_equ(vecn v1, vecn v2)** - equality between two vectors
* **bool vec3_neq(vec3 v1, vec3 v2)** - disequality between two vectors


* **float vecn_dot(vecn v1, vecn v2)** - dot product
* **float vecn_length_sqrd(vecn v)** - vector length squared
* **float vecn_length(vecn v)** - vector length
* **float vecn_dist_sqrd(vecn v1, vecn v2)** - distance between two vectors squared
* **float vecn_dist(vecn v1, vecn v2)** - distance between two vectors
* **float vecn_dist_manhattan(vecn v1, vecn v2)** - manhattan distance between two vectors
* **vec3 vec3_cross(vec3 v1, vec3 v2)** - cross product
* **vecn vecn_normalize(vecn v)** - normalize vector

* **vecn vecn_reflect(vecn v1, vecn v2)** - vector reflection
* **vec3 vec3_project(vec3 v1, vec3 v2)** - vector projection

* **vecn vecn_from_string(char\* s)** - get vector from string 
* **void vecn_print(vecn v)** - print vector

* **void vecn_to_array(vecn v, float\* out)** - transform vector into float array

* **vec4 vec3_to_homogeneous(vec3 v)** - not sure
* **vec3 vec4_from_homogeneous(vec4 v)** - not sure

* **int vecn_hash(vecn v)** - vector hash
* **int vecn_mix_hash(vecn v)** - vector hash with other method

* **vecn vecn_saturate(vecn v)** - saturate vector
* **vecn vecn_lerp(vecn v1, vecn v2, float amount)** - interpolate vector
* **vecn vecn_smoothstep(vecn v1, vecn v2, float amount)** - interpolate vector with smooth step
* **vecn vecn_smootherstep(vecn v1, vecn v2, float amount)** - interpolate vector with smoother step
* **vec4 vec4_nearest_interp(vec4 v1, vec4 v2, float amount)** - interpolate vector with nearest
* **vec4 vec4_binearest_interp(vec4 top_left, vec4 top_right, vec4 bottom_left, vec4 bottom_right, float x_amount, float y_amount)** - interpolate vector with binearest
* **vec4 vec4_bilinear_interp(vec4 top_left, vec4 top_right, vec4 bottom_left, vec4 bottom_right, float x_amount, float y_amount)** - interpolate vector with bilinear

### **quaternions**:
* **quat quat_id()** - creates identity quaternion
* **quat quat_new(float x, float y, float z, float w)** - creates quaternion
* **quat quat_from_euler(vec3 r)** - creates quaternion from euler
* **quat quat_angle_axis(float angle, vec3 axis)** creates quaternion with angle
* **quat quat_rotation_x(float angle)** - creates quaternion rotated at x axis
* **quat quat_rotation_y(float angle)** - creates quaternion rotated at y axis
* **quat quat_rotation_z(float angle)** - creates quaternion rotated at z axis
* **float quat_at(quat q, int i)** - gets quaternion element
**float quat_real(quat q)** - gets quaternion real element
**vec3 quat_imaginaries(quat q)** - gets quaternion imaginary elements
* **void quat_to_angle_axis(quat q, vec3* axis, float* angle)** - get angle and axis from quaternion
* **vec3 quat_to_euler(quat q)** - creates euler from quaternion
* **quat quat_neg(quat q)** - negates quaternion
* **float quat_dot(quat q1, quat q2)** - gets quaternion dot product 
* **quat quat_scale(quat q, float f)** - scales quaternion
* **quat quat_mul_quat(quat q1, quat q2)** - multiplies quaternions
* **vec3 quat_mul_vec3(quat q, vec3 v)** - multiply quaternion with vector
* **quat quat_inverse(quat q)** - inverts quaternion
* **quat quat_unit_inverse(quat q)** - inverts quaternion units
* **float quat_length(quat q)** - gets quaternion length
* **quat quat_normalize(quat q)** - normalizes quaternion

* **quat quat_exp(vec3 w)** - powers quaternion to w
* **vec3 quat_log(quat q)** - gets log from quaternion
* **quat quat_slerp(quat q1, quat q2, float amount)** - slerp quaternion

* **quat quat_constrain(quat q, vec3 axis)** - constrains quaternion with axis
* **quat quat_constrain_y(quat q)** - constrains y unit from quaternion

* **float quat_distance(quat q0, quat q1)** - gets distance between two quaternions
* **quat quat_interpolate(quat\* qs, float* ws, int count)** - interpolates quaternion array

* **quat_dual quat_dual_id()** - creates identity dual quaternion
* **quat_dual quat_dual_new(quat real, quat dual)** - creates dual quaternion
* **quat_dual quat_dual_transform(quat q, vec3 t)** - gets transformed quaternion as dual quaternion
* **quat_dual quat_dual_mul(quat_dual q0, quat_dual q1)** - multiplies dual quaternions
* **vec3 quat_dual_mul_vec3(quat_dual q, vec3 v)** - multiply dual quaternion with vector
* **vec3 quat_dual_mul_vec3_rot(quat_dual q, vec3 v)** - rotates dual quaternion with vector

### **matrix maths**
### note: matn stands for any matrix size 2-4, matn/n stands for two possible sizes, vecn stands for any vector size 2-4, vecn/n stands for two possible vector sizes


* **matn matn_id()** - creates identity matrix
* **matn matn_zero()** - creates empty matrix
* **matn matn_new(float xx, float xy, float yx, float yy,...)** - creates new matrix
* **mat2 matn_mul_matn(matn m1, matn mat2)**
* **vec2 matn_mul_vecn(mat2 m, vecn v)**

* **matn matn_transpose(matn m)**
* **float matn_det(matn m)**
* **mat2 mat2_inverse(mat2 m)**

* **void matn_to_array(matn m, float\* out)**
* **void matn_print(matn m)**
* **mat2 mat2_rotation(float a)**

* **mat3/4 mat3/4_scale(vec3 s)**

* **mat3/4 mat3/4_rotation_x(float a)**
* **mat3/4 mat3/4_rotation_y(float a)**
* **mat3/4 mat3/4_rotation_z(float a)**
* **mat3/4 mat3/4_rotation_angle_axis(float angle, vec3/4 axis)**

* **float mat4_at(mat4 m, int i, int j)**
* **mat4 mat4_set(mat4 m, int x, int y, float v)**


* **mat4 mat4_inverse(mat4 m)**

* **mat4 mat3_to_mat4(mat3 m)**
* **mat3 mat4_to_mat3(mat4 m)**
* **quat mat4_to_quat(mat4 m)**
* **quat_dual mat4_to_quat_dual(mat4 m)**

* **void mat4_to_array_trans(mat4 m, float\* out)**

* **mat4 mat4_translation(vec3 v)**

* **mat4 mat4_rotation_euler(float x, float y, float z)**
* **mat4 mat4_rotation_quat(quat q)**
* **mat4 mat4_rotation_quat_dual(quat_dual q)**

* **mat4 mat4_view_look_at(vec3 position, vec3 target, vec3 up)**
* **mat4 mat4_perspective(float fov, float near_clip, float far_clip, float ratio)**
* **mat4 mat4_orthographic(float left, float right, float bottom, float top, float near, float far)**

* **mat4 mat4_world(vec3 position, vec3 scale, quat rotation)**

* **mat4 mat4_lerp(mat4 m1, mat4 mat2, float amount)**
* **mat4 mat4_smoothstep(mat4 m1, mat4 mat2, float amount)**

#
### **geometry**:
### **plane**:

* **plane plane_new(vec3 position, vec3 direction)**
* **plane plane_transform(plane p, mat4 world, mat3 world_normal)**
* **plane plane_transform_space(plane p, mat3 space, mat3 space_normal)**
* **float plane_distance(plane p, vec3 point)**

* **bool point_inside_plane(vec3 point, plane p)**
* **bool point_outside_plane(vec3 point, plane p)**
* **bool point_intersects_plane(vec3 point, plane p)**

* **bool point_swept_inside_plane(vec3 point, vec3 v, plane p)**
* **bool point_swept_outside_plane(vec3 point, vec3 v, plane p)**
* **bool point_swept_intersects_plane(vec3 point, vec3 v, plane p)**

* **vec3 plane_closest(plane p, vec3 v)**
* **vec3 plane_project(plane p, vec3 v)**

### **box**:

* **box box_new(float x_min, float x_max, float y_min, float y_max, float z_min, float z_max)**
* **box box_sphere(vec3 center, float radius)**
* **box box_merge(box b1, box b2)**
* **box box_transform(box b1, mat4 world, mat3 world_normal)**
* **box box_invert(box b)**
* **box box_invert_depth(box b)**
* **box box_invert_width(box b)**
* **box box_invert_height(box b)**

* **bool point_inside_box(vec3 point, box b)**
* **bool point_outside_box(vec3 point, box b)**
* **bool point_intersects_box(vec3 point, box b)**

### **frustum**:


* **frustum frustum_new(vec3 ntr, vec3 ntl, vec3 nbr, vec3 nbl, vec3 ftr, vec3 ftl, vec3 fbr, vec3 fbl)**
* **frustum frustum_new_clipbox()**
* **frustum frustum_new_camera(mat4 view, mat4 proj)**
* **frustum frustum_slice(frustum f, float start, float end)**
* **frustum frustum_transform(frustum f, mat4 m)**
* **frustum frustum_translate(frustum f, vec3 v)**

* **vec3 frustum_center(frustum f)**
* **vec3 frustum_maximums(frustum f)**
* **vec3 frustum_minimums(frustum f)**

* **box frustum_box(frustum f)**

* **bool frustum_outside_box(frustum f, box b)**

### **sphere**:

* **sphere sphere_unit()**
* **sphere sphere_point()**
* **sphere sphere_new(vec3 center, float radius)**
* **sphere sphere_merge(sphere s1, sphere s2)**
* **sphere sphere_merge_many(sphere\* s, int count)**
* **sphere sphere_transform(sphere s, mat4 world)**
* **sphere sphere_translate(sphere s, vec3 x)**
* **sphere sphere_scale(sphere s, float x)**
* **sphere sphere_transform_space(sphere s, mat3 space)**

* **sphere sphere_of_box(box bb)**
* **sphere sphere_of_frustum(frustum f)**

* **bool sphere_inside_box(sphere s, box b)**
* **bool sphere_outside_box(sphere s, box b)**
* **bool sphere_intersects_box(sphere s, box b)**

* **bool sphere_inside_frustum(sphere s, frustum f)**
* **bool sphere_outside_frustum(sphere s, frustum f)**
* **bool sphere_intersects_frustum(sphere s, frustum f)**

* **bool sphere_outside_sphere(sphere s1, sphere s2)** 
* **bool sphere_inside_sphere(sphere s1, sphere s2)** 
* **bool sphere_intersects_sphere(sphere s1, sphere s2)** 

* **bool point_inside_sphere(sphere s, vec3 point)**
* **bool point_outside_sphere(sphere s, vec3 point)**
* **bool point_intersects_sphere(sphere s, vec3 point)**

* **bool line_inside_sphere(sphere s, vec3 start, vec3 end)**
* **bool line_outside_sphere(sphere s, vec3 start, vec3 end)**
* **bool line_intersects_sphere(sphere s, vec3 start, vec3 end)**

* **bool sphere_inside_plane(sphere s, plane p)**
* **bool sphere_outside_plane(sphere s, plane p)**
* **bool sphere_intersects_plane(sphere s, plane p)**
* **bool sphere_intersects_plane_point(sphere s, plane p, vec3\* point, float\* radius)**

* **bool point_swept_inside_sphere(sphere s, vec3 v, vec3 point)**
* **bool point_swept_outside_sphere(sphere s, vec3 v, vec3 point)**
* **bool point_swept_intersects_sphere(sphere s, vec3 v, vec3 point)**

* **bool sphere_swept_inside_plane(sphere s, vec3 v, plane p)**
* **bool sphere_swept_outside_plane(sphere s, vec3 v, plane p)**
* **bool sphere_swept_intersects_plane(sphere s, vec3 v, plane p)**

* **bool sphere_swept_outside_sphere(sphere s1, vec3 v, sphere s2)** 
* **bool sphere_swept_inside_sphere(sphere s1, vec3 v, sphere s2)** 
* **bool sphere_swept_intersects_sphere(sphere s1, vec3 v, sphere s2)** 

* **bool point_inside_triangle(vec3 p, vec3 v0, vec3 v1, vec3 v2)**
* **bool sphere_intersects_face(sphere s, vec3 v0, vec3 v1, vec3 v2, vec3 norm)**

### **ellipsoid**:

* **ellipsoid ellipsoid_new(vec3 center, vec3 radiuses)**
* **ellipsoid ellipsoid_transform(ellipsoid e, mat4 m)**
* **ellipsoid ellipsoid_of_sphere(sphere s)**

* **mat3 ellipsoid_space(ellipsoid e)**
* **mat3 ellipsoid_inv_space(ellipsoid e)**


* **capsule capsule_new(vec3 start, vec3 end, float radius)**
* **capsule capsule_transform(capsule c, mat4 m)**

* **bool capsule_inside_plane(capsule c, plane p)**
* **bool capsule_outside_plane(capsule c, plane p)**
* **bool capsule_intersects_plane(capsule c, plane p)**

### **vertex**:

* **vertex vertex_new()**
* **bool vertex_equal(vertex v1, vertex v2)**
* **void vertex_print(vertex v)**

### **mesh**:

* **mesh\* mesh_new()**
* **void mesh_delete(mesh\* m)**

* **void mesh_generate_normals(mesh\* m)**
* **void mesh_generate_tangents(mesh\* m)**
* **void mesh_generate_orthagonal_tangents(mesh\* m)**
* **void mesh_generate_texcoords_cylinder(mesh\* m)**

* **void mesh_print(mesh\* m)**
* **float mesh_surface_area(mesh\* m)**

* **void mesh_transform(mesh\* m, mat4 transform)**
* **void mesh_translate(mesh\* m, vec3 translation)**
* **void mesh_scale(mesh\* m, float scale)**

* **sphere mesh_bounding_sphere(mesh\* m)**

### **model**:
* **model\* model_new()**
* **void model_delete(model\* m)**

* **void model_generate_normals(model\* m)**
* **void model_generate_tangents(model\* m)**
* **void model_generate_orthagonal_tangents(model\* m)**
* **void model_generate_texcoords_cylinder(model\* m)**

* **void model_print(model\* m)**
* **float model_surface_area(model\* m)**

* **void model_transform(model\* m, mat4 transform)**
* **void model_translate(model\* m, vec3 translation)**
* **void model_scale(model\* m, float scale)**

### **triangle**:

* **vec3 triangle_tangent(vertex v1, vertex v2, vertex v3)**
* **vec3 triangle_binormal(vertex v1, vertex v2, vertex v3)**
* **vec3 triangle_normal(vertex v1, vertex v2, vertex v3)**
* **vec3 triangle_random_position(vertex v1, vertex v2, vertex v3)**
* **float triangle_area(vertex v1, vertex v2, vertex v3)**

* **float triangle_difference_u(vertex v1, vertex v2, vertex v3)**
* **float triangle_difference_v(vertex v1, vertex v2, vertex v3)**

* **vertex triangle_random_position_interpolation(vertex v1, vertex v2, vertex v3)**

### **tweeeners**:

* **float tween_approach(float curr, float target, float timestep, float steepness)**
* **float tween_linear(float curr, float target, float timestep, float max)**

* **vec3 vec3_tween_approach(vec3 curr, vec3 target, float timestep, float steepness)**
* **vec3 vec3_tween_linear(vec3 curr, vec3 target, float timestep, float max)**



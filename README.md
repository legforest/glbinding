glbinding
====

glbinding is an automatically generated C++ binding for OpenGL (using the gl.xml).
The implementation uses modern C++11 features like enum classes, lambdas and variadic templates.
All defined OpenGL symbols are real functions and variables, they don't rely on macros.
It should serve as an alternative to other OpenGL bindings like GLEW [1] and glad [2].

The standard glbinding API setup looks like
```
#include <glbinding/gl/gl.h>
#include <glbinding/glbinding.h>

using namespace gl;

int main()
{
  // create context, e.g. using GLFW, Qt, SDL, GLUT, ...
  
  glbinding::initialize();
  
  glBegin(GL_TRIANGLES);
  // ...
  glEnd();
}
```

Current code written with a typical C binding for OpenGL (e.g. GLEW) is fully compatible for the use with glbinding.
Just replace all includes to the old binding with the include to glbinding and use the ```gl``` namespace.
Besides the actual binding, glbinding comes with these additional features:
* Per OpenGL Feature API headers (e.g. gl44core.h)
  * Core, extensions, combined
  * Per feature functions and constants (enums, bitfields, special values)
  * Separate namespaces
* Type-safe OpenGL parameters (enums, bitfields, bitfield groups)
  * Never mix bitfields of different groups again
  * Code completion for all allowed values
* Global callbacks
  * Never forget glGetError() again
  * Logging all OpenGL calls
* Per function callbacks
* Meta information about the generated OpenGL binding and the OpenGL runtime
  * OpenGL extension support
    * Since when is an extension in the core profile?
    * Is an extension supported by the current context?
    * Collect all supported extensions as list of enums
  * GL symbol to string conversion
  * string to GL symbol conversion
* Multi-context support (explicit switch required)
* Multi-threading support

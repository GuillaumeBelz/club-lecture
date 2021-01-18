note:

- https://github.com/topics/game-engine (categorie game engine sur github)
- https://github.com/Aredhele (essais de game engine
- https://github.com/leereilly/games (liste de jeux)
- https://github.com/kripken/BananaBread (FPS simple)
- https://github.com/assaultcube/AC (FPS simple)

# Game Engine Architecture, 3ème édition
# Part I - Foundations
## Chapitre 1: Introduction

Runtime Engine Architecture:
- hardware, drivers, OS
- Third-Party SDKs and Middleware
  - Data Structures and Algorithms : boost, folly, loki, EA
  - Graphics : OpenGL, Metal, Vulkan, DirectX
  - Collision and Physics : Havok, PhysX, ODE
  - Character Animation: Granny, HavokAnim, OrbisAnim
  - Biomechanical Character Models
- Platform Independence Layer
- Core: assert, memory managment,  math lib, data struct and algos
- Resource Manager
- Rendering Engine
  - Low-Level Renderer: GDI, materials, shaders, lighting, cameras, texts, primitives, scenes, texture, debug
  - Scene Graph/Culling Optimizations: spatial hash, occulusion, LOD
  - Visual Effects: light mapping, dynamic shadows, HDR, subscattering, particules, post effects, environment mapping
  - Front End: HUD, FMV, IGC, GUI, menus
  - Profiling and Debugging Tools: recording, playback, stats. VTune, Insure++, Valgrind
  - Collision and Physics: forces, rigid bodies, collidables, ray casting, phantoms, collisions
  - Animation: trees, IK, post process, blending, playback, sub-skeletal
  - HID
  - Audio: DSP, effects, 3D, playback
  - Online Multiplayer/Networking
  - Gameplay Foundation Systems: FSM, script, worlds and object models, events, AI
- Game-Specific Subsystems

Tools and the Asset Pipeline:
- Digital Content Creation Tools
- The Asset Conditioning Pipeline
- The World Editor
- The Resource Database

## Chapitre 2: Tools of the Trade

- version control
- compilers, IDE
- profiling
- memory leaks/corruption

## Chapitre 3: Fundamentals of Software Engineering for Games

**C++ Review and Best Practices**

- heritage = is-a, composition = has-a, aggregation = uses-a

**Catching and Handling Errors**

- assert:
```cpp
#if ASSERTIONS_ENABLED
// define some inline assembly that causes a break
// into the debugger -- this will be different on each // target CPU
#define debugBreak() asm { int 3 }

// check the expression and fail if it is false 
#define ASSERT(expr) \
  if (expr) { } \ 
  else { \
    reportAssertionFailure(#expr, __FILE__, __LINE__); \
    debugBreak(); \ 
  }
#else
#define ASSERT(expr) // evaluates to nothing #endif
```

- static assert:
```cpp
#define _ASSERT_GLUE(a, b)  a ## b
#define ASSERT_GLUE(a, b) _ASSERT_GLUE(a, b)

#define STATIC_ASSERT(expr) \ 
  enum { \
    ASSERT_GLUE(g_assert_fail_, __LINE__) = 1 / (int)(!!(expr)) \
  }
  
STATIC_ASSERT(sizeof(int) == 4); // should pass 
STATIC_ASSERT(sizeof(float) == 1); // should fail
```

**Data, Code and Memory Layout**

**Computer Hardware Fundamentals**

**Memory Architectures**

## Chapitre 4: Parallelism and Concurrent Programming

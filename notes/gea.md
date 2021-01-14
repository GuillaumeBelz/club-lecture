
# Game Engine Architecture, 3ème édition
# Part I - Foundations
## Chapitre 1: Introduction

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


# Tour of C++, 2ème édition
## Chapitre 1: The Basics

C++ Core Guidelines

- [1] Don’t panic! All will become clear in time; §1.1; [CG: In.0].
- [2] Don’t use the built-in features exclusively or on their own. On the contrary, the fundamental (built-in) features are usually best used indirectly through libraries, such as the ISO C++ standard library (Chapters 8–15); [CG: P.10].
- [3] You don’t have to know every detail of C++ to write good programs.
- [4] Focus on programming techniques, not on language features.
- [5] For the final word on language definition issues, see the ISO C++ standard; §16.1.3; [CG:P.2].
- [6] ‘‘Package’’ meaningful operations as carefully named functions; §1.3; [CG: F.1].
- [7] A function should perform a single logical operation; §1.3 [CG: F.2].
- [8] Keep functions short; §1.3; [CG: F.3].
- [9] Use overloading when functions perform conceptually the same task on different types; §1.3.
- [10] If a function may have to be evaluated at compile time, declare it constexpr; §1.6; [CG: F.4].
- [11] Understand how language primitives map to hardware; §1.4, §1.7, §1.9, §2.3, §4.2.2, §4.4.
- [12] Use digit separators to make large literals readable; §1.4; [CG: NL.11].
- [13] Avoid complicated expressions; [CG: ES.40].
- [14] Avoid narrowing conversions; §1.4.2; [CG: ES.46].
- [15] Minimize the scope of a variable; §1.5.
- [16] Avoid ‘‘magic constants’’; use symbolic constants; §1.6; [CG: ES.45].
- [17] Prefer immutable data; §1.6; [CG: P.10].
- [18] Declare one name (only) per declaration; [CG: ES.10].
- [19] Keep common and local names short, and keep uncommon and nonlocal names longer; [CG:ES.7].
- [20] Avoid similar-looking names; [CG: ES.8].
- [21] Avoid ALL_CAPS names; [CG: ES.9].
- [22] Prefer the {}-initializer syntax for declarations with a named type; §1.4; [CG: ES.23].
- [23] Use auto to avoid repeating type names; §1.4.2; [CG: ES.11].
- [24] Avoid uninitialized variables; §1.4; [CG: ES.20].
- [25] Keep scopes small; §1.5; [CG: ES.5].
- [26] When declaring a variable in the condition of an if-statement, prefer the version with the implicit test against 0; §1.8.
- [27] Use unsigned for bit manipulation only; §1.4; [CG: ES.101] [CG: ES.106].
- [28] Keep use of pointers simple and straightforward; §1.7; [CG: ES.42].
- [29] Use nullptr rather than 0 or NULL; §1.7; [CG: ES.47].
- [30] Don’t declare a variable until you have a value to initialize it with; §1.7, §1.8; [CG: ES.21].
- [31] Don’t say in comments what can be clearly stated in code; [CG: NL.1].
- [32] State intent in comments; [CG: NL.2].
- [33] Maintain a consistent indentation style; [CG: NL.4].


## Chapitre 2: User-Defined Types




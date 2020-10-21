# notes
* modules beginning - [Modules the beginner's guide - Daniela Engert - Meeting C++ 2019](https://www.youtube.com/watch?v=Kqo-jIq4V3I&t=3067s)
* Bryce really good explanation - [Modules are coming - Bryce Adelstein Lelbach - Meeting Cpp 2019](https://www.youtube.com/watch?v=yee9i2rUF3s)
* [Paper on tooling impact](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0804r0.html)


* Modules information from the Soup (build system) creators - https://github.com/mwasplund/Soup/blob/master/Docs/Proposal.md

* modules gcc branch - they say CMI/BMI is not distributable (just a cache) - https://gcc.gnu.org/wiki/cxx-modules - tight to the version of the compiler, as thats AST representation and it can change between versions

* modules satisfy 3 rules of Essential Physical Design (no cycles, no long-distance, no transitive) - https://www.youtube.com/watch?v=K_fTl_hIEGY&t=631s

* CppCon 2016: Manuel Klimek “Deploying C++ modules to 100s of millions of lines of code":
 * initially no speed up (was it protobuf having too much dependecncy, need ot recheck)
 * speedup per compilation unit, but increased dependency inputs 37:15, naive dependency graph), but it also seems they were building, not reusing cache? 
 * slowdorn on staging, sending for remote building - they say they'd have to send all modules header files? Solution is only to split libraries (which internally allow you to have cyclic dependencies, which is bad)
 * modules kind of help not using the PIMPL pattern (if it's used for build speed improvements); won't be useful for ABI

Papers:
* modules build-systems usability: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1427r0.pdf  
* http://open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1948r0.pdf - modules participate in the name mangling - API & ABI

CMake support:
* https://gitlab.kitware.com/cmake/cmake/-/issues/18355

Packaging, not fully read yet:
* http://open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1788r3.pdf
* Richard -> http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1767r0.html

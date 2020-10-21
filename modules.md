# notes
* modules beginning - [Modules the beginner's guide - Daniela Engert - Meeting C++ 2019](https://www.youtube.com/watch?v=Kqo-jIq4V3I&t=3067s)
* Bryce really good explanation - [Modules are coming - Bryce Adelstein Lelbach - Meeting Cpp 2019](https://www.youtube.com/watch?v=yee9i2rUF3s)
* [Paper on tooling impact](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0804r0.html)

* C++Now 2019: Richárd Szalay “The Rough Road Towards Upgrading to C++ Modules”
  * problems with migration to modules

* Modules information from the Soup (build system) creators - https://github.com/mwasplund/Soup/blob/master/Docs/Proposal.md

* modules gcc branch - they say CMI/BMI is not distributable (just a cache) - https://gcc.gnu.org/wiki/cxx-modules - tight to the version of the compiler, as thats AST representation and it can change between versions

* modules satisfy 3 rules of Essential Physical Design (no cycles, no long-distance, no transitive) - https://www.youtube.com/watch?v=K_fTl_hIEGY&t=631s

* CppCon 2016: Manuel Klimek “Deploying C++ modules to 100s of millions of lines of code":
 * initially no speed up (was it protobuf having too much dependecncy, need ot recheck)
 * speedup per compilation unit, but increased dependency inputs 37:15, naive dependency graph), but it also seems they were building, not reusing cache? 
 * slowdorn on staging, sending for remote building - they say they'd have to send all modules header files? Solution is only to split libraries (which internally allow you to have cyclic dependencies, which is bad)
 * modules kind of help not using the PIMPL pattern (if it's used for build speed improvements); won't be useful for ABI

* C++ Modules and Large-Scale Development
  * No cyclic dependencies
  * Long distance friendships

  * insulation (encapsulation - change doesn't affect other changes in code; insulation - change doesn't require recompilation) - modules don't give insulation (because that's slowness, otherwise performance cost)
  * including header in a header (isA, hasA, inline function body, enumberations, template)

  * to estabilish physical dependency we do #include, if there's none it should be forward dceclared

  * we wantn to make modules possible (migration path existss, additive way, interoperable) - some group modules and others header files 
  * logical encapsulations (headers symulate, modules do) - things not exported so the encapsulation is there; insulation not

  * modules include transitive usage of headers

* CppCon 2016: Richard Smith “There and Back Again: An Incremental C++ Modules Design"
 * he talks about the TS giving following:
  * instead of headers -> module interface units
  * nothing exported by default
  * first class import syntax
  * module ownership semaantics - name collisions fixed

Papers:
* modules build-systems usability: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1427r0.pdf  
* http://open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1948r0.pdf - modules participate in the name mangling - API & ABI

CMake support:
* https://gitlab.kitware.com/cmake/cmake/-/issues/18355

Packaging, not fully read yet:
* http://open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1788r3.pdf
* Richard -> http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1767r0.html

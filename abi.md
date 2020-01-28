# notes

http://gernotklingler.com/blog/creating-using-shared-libraries-different-compilers-different-operating-systems/
  libraries, but shows how  
  
https://www.youtube.com/watch?v=JPQWQfDhICA
  CppCon 2017: James McNellis “Everything You Ever Wanted to Know about DLLs”
  
https://www.youtube.com/watch?v=dOfucXtyEsU
  CppCon 2018: Matt Godbolt “The Bits Between the Bits: How We Get to main()”

std::string in gcc changing to c++11, 

Titus paper

Interoperability example: https://hsivonen.fi/modern-cpp-in-rust/
Binary compatibility of shared libraries: http://syrcose.ispras.ru/2009/files/02_paper.pdf
How to write shared libraries - Urich Drepper

Wine calling conventions: https://www.codeweavers.com/about/blogs/aeikum/2016/12/2/creating-visual-studio-c-objects-in-wine

* gcc-4.7.2-1-mingw32.README.txt - changed default flags - ABI
* In the GCC 5.1 release libstdc++ introduced a new library ABI that includes new implementations of std::string and std::list. These changes were necessary to conform to the 2011 C++ standard which forbids Copy-On-Write strings and requires lists to keep track of their size.
* clang on msvc compatibility https://clang.llvm.org/docs/MSVCCompatibility.html
* C++ std library problem it's a standard TEMPLATE library


Problems:
* getting precompiled binaries (package management)
* using your binary with deps on older systems (or a range of systems)
* language interoperability

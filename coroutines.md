# notes
Nice presentation from MIMUW http://cpp.mimuw.edu.pl/files/await-yield-c++-coroutines.pdf
Might be interesting to read: https://blog.panicsoftware.com/co_awaiting-coroutines/

Good talk by James McNellis: https://www.youtube.com/watch?v=ZTqHjjm86Bw&t=1238s
Awesome talk with live demos by Gor Nishanov: https://www.youtube.com/watch?v=UL3TtTgt3oU&t=1676s 
CppCon 2017: David Sackstein shows differences between different approaches (+fibers) https://www.youtube.com/watch?v=mCD6VLVS_y4

Few good articles: https://lewissbaker.github.io - this guy also implemented cppcoro https://github.com/lewissbaker/cppcoro

Some code by GOR: https://wandbox.org/permlink/Xb1Lu7DMmm1NVkNC
Got about impact: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0975r0.html

To be read:
https://www.reddit.com/r/cpp/comments/6ly4rz/it_had_to_be_done_abusing_co_await_for_optionals/

Stackless implementation details:
* backround: https://youtu.be/_fu0gx-xseY?t=103
* details: https://youtu.be/8C8NnE1Dg4A?t=572

Coroutines are about Inversion of control (but that's rather for generators): https://hackernoon.com/c-coroutine-ts-its-about-inversion-of-control-d1588c4c4c31 

Qt Signals-Slots using coroutines: http://jefftrull.github.io/qt/c++/coroutines/2018/07/21/coroutines-and-qt.html

Arthur O'Dwyer header-only library for coroutines https://github.com/Quuxplusone/coro
-fcoroutines-ts --std=c++2a -stdlib=libc++ -lc++abi
Go-like channels using C++ coroutines:
* Jon Balenda's CppCon 2016 talk - https://www.youtube.com/watch?v=N3CkQu39j5I
* https://luncliff.github.io/coroutine/articles/designing-the-channel/

Dev.to good intro: https://dev.to/dwd/coroutines-in-c-2i5b

Gor paper with examples: http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4287.pdf
http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1492r0.pdf

Symmetrical coroutines: http://open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0913r0.html
Potential implementation with networking library: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0055r0.html

Use cases & concens by Google​
37
Google expressing concerns: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0973r0.pdf: http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0973r0.pdf

task<T> -> could be used for lazy comutations, if that's not for async stuff
  
  Good links list: https://gist.github.com/MattPD/9b55db49537a90545a90447392ad3aeb

Disadvantages:
* RAII might be not doing what you expect
* Harder debugging
* Parts of coroutine executed on different threadsin 
* Captured variables not visible

--------------------------------
REALLY GOOD step by step tutorial: https://kirit.com/How%20C%2B%2B%20coroutines%20work
--------------------------------


* Presentation:
 * show stack trace
 * currently no tooling for seeing stored structures by handle

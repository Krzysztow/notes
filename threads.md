# Locks for preventing data races:
* simple mutex - exclusive access, best locked with RAII:
 * `lock_guard` - the simplest RAII
 * `unique_lock` - moveable, one resource only; like `unique_ptr`; when owns mutex and d'tor called, unlocks the mutex
* reader/writer lock - in c++11 not implemented - use `boost::shared_mutex` instead, with `lock_guard` and `unique_lock`. Available in c++17.
* locking of resources only once, e.g. used for lazy initialization - `once_flag` with `call_once(once_flag, fct, args...)`
* `std::recursive_mutex` - when same thread is allowed for locking multiple times. 
Note: when trying to lock multiple locks - `std::lock(lockable...)` - with deadlock avoidance algorithm, unlocks all on exception. In such case use `std::adopt_lock`
Note: problematic, when there's a need to lock more than one mutex. Possible deadlock. Usually, best to preserve the order - hierarchical lock migth be a solution.
Note: `static thread_local T` - might be used to get instance of the type per thread

# Synchronization between threads:
* `std::condition_variable` - works only with `std::mutex`
 * notify with `condition_variable::notify_one()`
* `std::condition_variable_any` - works with many mutex-like types, but might have extra overhead

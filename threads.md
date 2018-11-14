# Locks for preventing data races:
* simple mutex - exclusive access, best locked with RAII:
 * `lock_guard` - the simplest RAII - cannot unlock it manually
 * `unique_lock` - moveable, one resource only; like `unique_ptr`; when owns mutex and d'tor called, unlocks the mutex
* reader/writer lock - in c++11 not implemented - use `boost::shared_mutex` instead, with `lock_guard` and `unique_lock`. Available in c++17.
* locking of resources only once, e.g. used for lazy initialization - `once_flag` with `call_once(once_flag, fct, args...)`
* `std::recursive_mutex` - when same thread is allowed for locking multiple times. 
Note: when trying to lock multiple locks - `std::lock(lockable...)` - with deadlock avoidance algorithm, unlocks all on exception. In such case use `std::adopt_lock`
Note: problematic, when there's a need to lock more than one mutex. Possible deadlock. Usually, best to preserve the order - hierarchical lock migth be a solution.
Note: `static thread_local T` - might be used to get instance of the type per thread

# Synchronization between threads:
* condition variables:
 * `std::condition_variable` - works only with `std::mutex`. Looks like below. There might be spurious wakes (without notify being sent) and checks for a condition satisfaction.
```
std::lock_guard<std::mutex> lk(mut);
//do exclusive work
data_cond.notify_one();
```
and on another thread:
```
std::unique_lock<std::mutex> lk(mut);
data_cond.wait(lk, [](return condSatisfied();));
//do exclusive work
lk.unlock();
```
  * notify with `condition_variable::notify_one()` or `condition_variable::notify_all()`
 * `std::condition_variable_any` - works with many mutex-like types, but might have extra overhead
* if the waiting happens only once, it's worth considering the future. 
 * `std::future<T>`, `std::shared_future<T>` - returned from `std::async()`. `std::future<T>::get()` blocks and waits for a future to become ready. Async call might be deferred or run asynchronously.
 * `std::future<T>` may be aso returned from `std::packaged_task<ret(args...)>, to which we might associate callable and call it on any thread one wants.
```
std::promise result_promise;
std::future<T> result_future = result_promise.get_future();
std::thread work_thread{doWork, std::move(result_future)};
T r = result_future.get();//also implicitly does future::wait()
work_thread.join();
```
and the work function:
```
void doWork(std::promise<T> promise) {
    //some work to get result
    promise.set_value(result);
}
```

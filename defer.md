# Defer

In Go, a defer statement is similar to `final` or `ensure` in other programming language out there. It simply used for a cleanup for a function and most programming languages guarantee its execution at the end of function call or even when there are errors.

This can be used where we need to do some cleanup, like unsubscribe from a channel or close database connection etc.




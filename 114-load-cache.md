# Load cache from a latter code chunk

Sometimes we may want to insert an object value early in the document, when the object has not been created. [For example](http://stackoverflow.com/q/18581027/559676), you may want to mention a result in your abstract using an inline R expression, but the result is calculated later in the report.

One solution is to `save()` the workspace in a `.RData` file in the end of the document, and `load()` it in the beginning, e.g.


``` r
x = "NOT YET AVAILABLE"  # an object to be used
if (file.exists("everything.RData")) load("everything.RData")
```

In the end of the document, you save the workspace:


``` r
save.image("everything.RData")
```

Then you can use `` `r x` `` after `everything.RData` is loaded. When it is not available, you will see `x` as `NOT YET AVAILABLE`.

The function `load_cache()` is an alternative solution, which allows you to load the value of an object from a specific code chunk, when the chunk has been cached.

For example, there is no object called `y` that has been created in this document yet, but we can still insert it here: `6.2832`, as long as it will be created in the code chunk with the label `test-a` later.


``` r
y = 2 * pi
```

The first time you compile the document, you will see `y` is `NOT AVAILABLE`, but when you compile it for the second time, you will see its value `6.2832`.

You do not have to specify the object name in `load_cache()`, in which case the database will just be loaded, and you can use any objects available in the database as if they had been computed by the code chunk later.

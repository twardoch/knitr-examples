# A Knitr "Polyglot" Example for Markdown

This is a minimal example of using "polyglot"" **knitr** to produce an _HTML_ page from _Markdown_.


``` r
knitr::opts_chunk$set(engine.opts = list(perl = "-Mstrict -Mwarnings -Mfeature=say",
    bash = "-o errexit -o nounset"))
toTest <- c("R", "python", "scala", "bash", "perl")
where <- Sys.which(toTest)
```

## Engine runtime paths


``` r
for (n in names(where)) {
    path <- where[n]
    if (nchar(path) <= 0) {
        path <- "<not found>"
    }
    message("* __", n, "__: `", path, "`\n")
}
```

## Input Data

Pass the string to transform to engine subprocess via environment variable.


``` r
Sys.setenv(SOMETHING = "something")
```

## Compute Something in R


``` r
something <- Sys.getenv("SOMETHING")
somethingelse <- paste(something, "+ R")
cat(paste("'", something, "' is now '", somethingelse, "'", sep = ""))
```

```
R> 'something' is now 'something + R'
```

## Compute Something in Scala

Running small fragments without caching can take some time, as the Scala compiler has to launch and compile the script to JVM bytecode. The `-savecompiled` option (passed via `engine.opts`) will result in Scala caching the compiled script outside of _knitr_.


``` scala
val something = System.getenv("SOMETHING")
val somethingelse = something + " + Scala"
println("'" + something + "' is now '" + somethingelse + "'")
```

```
Scala> 'something' is now 'something + Scala'
```

## Compute Something in Python


``` python
import os
something = os.getenv("SOMETHING")
somethingelse = something + " + Python"
print("'" + something + "' is now '" + somethingelse + "'")
```

```
Python> 'something' is now 'something + Python'
```

## Compute Something in Bash


``` bash
something=$SOMETHING
somethingelse="$something + Bash"
echo "'$something' is now '$somethingelse'"
```

```
Bash> 'something' is now 'something + Bash'
```

## Compute Something in Perl


``` perl
my $something = $ENV{SOMETHING};
$something .= ' + Perl';
say join ' ', qw{something is now}, "'$something'";
```

```
Perl> something is now 'something + Perl'
```

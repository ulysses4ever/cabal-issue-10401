## Cabal issue [#10401](https://github.com/haskell/cabal/issues/10401)

``` shellsession
❯  ghc --version
The Glorious Glasgow Haskell Compilation System, version 9.6.5

❯ cabal --version
cabal-install version 3.10.3.0
compiled using version 3.10.3.0 of the Cabal library 

❯ cat app/Main.hs 
f = 1 + a

main = f + g

❯ cabal clean && cabal run exe:cabal-flags
Resolving dependencies...
Build profile: -w ghc-9.6.5 -O1
In order, the following will be built (use -v for more details):
 - cabal-flags-0.1.0.0 (exe:cabal-flags) (first run)
Configuring executable 'cabal-flags' for cabal-flags-0.1.0.0..
Preprocessing executable 'cabal-flags' for cabal-flags-0.1.0.0..
Building executable 'cabal-flags' for cabal-flags-0.1.0.0..
[1 of 1] Compiling Main             ( app/Main.hs, /home/artem/tmp/cabal-flags/dist-newstyle/build/x86_64-linux/ghc-9.6.5/cabal-flags-0.1.0.0/x/cabal-flags/build/cabal-flags/cabal-flags-tmp/Main.o )

app/Main.hs:3:12: error: [GHC-88464] Variable not in scope: g
  |
3 | main = f + g
  |            ^

app/Main.hs:1:9: error: [GHC-88464] Variable not in scope: a
  |
1 | f = 1 + a
  |         ^
```

The default prelude should be evaluated for every environment, that means the default and any named
one.

This is run with `--prelude default.ml --prelude a:a.ml --prelude b:b.ml`.
`default.ml` defines `let x = 1`. We should be able to reuse `x` in other envs:

```ocaml
# x
- : int = 1
```

<!-- $MDX env=a -->
```ocaml
# x + y
Line 1, characters 1-2:
Error: Unbound value x
```

<!-- $MDX env=b -->
```ocaml
# x + y
Line 1, characters 1-2:
Error: Unbound value x
```

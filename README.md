# Symbolic tests for curve25519-dalek

This is a fork of [curve25519-dalek][dalek] that provides an example of
symbolic testing with [`crux-mir`][mir-verifier], as shown in the [`crux-mir`
demo video][video].

[dalek]: https://github.com/dalek-cryptography/curve25519-dalek/
[mir-verifier]: https://github.com/GaloisInc/mir-verifier/issues
[video]: https://www.youtube.com/watch?v=dCNQFHjgotU

The concrete and symbolic `add_correct` tests appear near the bottom of
[`u64/scalar.rs`][scalar].  To run the test, first [set up `crux-mir`][setup],
then run:

```
cargo crux-test add_correct -- -s z3
```

This will run the symbolic `add_correct` test using the Z3 solver backend.
Z3 performs much better on this test than the default Yices backend does.

[scalar]: src/backend/serial/u64/scalar.rs
[setup]: https://github.com/GaloisInc/mir-verifier/issues#preliminaries

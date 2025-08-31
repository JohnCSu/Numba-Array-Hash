# Numba Array Hash

Simple Implementaion of hashing that works for arrays of any shape or type that numba accepts in no python mode. This is primarily used in numba nopython mode
(njit) so arrays can effectively be used as keys for typed Dict in numba.

Uses the old hashing algorithim by python. Can be seen in python 3.7 code here:
https://github.com/python/cpython/blob/v3.7.0/Objects/tupleobject.c#L348 

Newer Python versions use xxHash (https://github.com/Cyan4973/xxHash) for tuplehash, but the old hashing algorithim should be sufficient to be used with numba dicts (and is significantly easier to understand and implement)

## How it works

The array is first flattened and then passed into the hashing algorithim so functionally behaves like tuplehash in older python versions.

 Note that because the `ndarray.ravel()` is used to turn the array into a 1D array, the order of the array (e.g C for row major, F for column major) will produce different hashes.

## Warning: no mutability or type checks
It is upto the user to ensure that the array being hashed makes sense i.e. array is considered immutable, and elements being hashed makes sense.

- Integer or fixed string types recommended

## Packages
Any compatible numba and numpy package

## License
MIT
 



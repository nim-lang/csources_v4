# csources_v4
CSources compiled from Nim version 2.4.1. Based on https://github.com/nim-lang/Nim/commit/1cc36fb0f54273d530d5a1751d7b03b626d395f2

## How these sources were generated

The C code is the output of `koch csource -d:danger` (the default ORC memory
management, all runtime checks off), run in a Nim checkout named `nimv2` that
sits next to this repository:

```
cd ..
git clone https://github.com/nim-lang/Nim nimv2
cd nimv2
git checkout 1cc36fb0f54273d530d5a1751d7b03b626d395f2
./build_all.sh             # bootstraps and fetches dist/checksums and dist/nimony,
                           # which `koch csource` needs but does not clone itself
./koch csource -d:danger   # writes the C sources to build/
cd ../csources_v4
nim r push_c_code.nim      # copies ../nimv2/build here and `git add`s it
```

`push_c_code.nim` also copies `build/empty.txt`, which is not part of this
repository; delete it before committing.

To update to a newer Nim, check out the new commit in `nimv2`, rerun the steps
above and update the commit hash in this README.

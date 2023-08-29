# Fuzzing with Fuzzilli

Get Fuzzilli
```shell
git clone https://github.com/googleprojectzero/fuzzilli.git
```

Setup Profiles for Hermes
```shell
mv profile/*.swift $FUZZILLI_LOCATION/Sources/FuzzilliCli/Profiles/
```

Build Instrumented Binary
```shell
mkdir fuzzilli_build && cd fuzzilli_build
export CC=clang
export CXX=clang++
cmake .. -DHERMES_ENABLE_FUZZILLI=ON -DHERMES_ENABLE_TRACE_PC_GUARD=ON $OTHER_FLAGS
make fuzzilli
```

Start Fuzzing:
```shell
cd $FUZZILLI_LOCATION
swift run  FuzzilliCli --profile=hermes --engine=hybird $BINARY_LOCATION --storagePath=$CRASH_LOCATION --overwrite
```

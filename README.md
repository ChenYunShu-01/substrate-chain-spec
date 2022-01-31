1. Compile benchmark 
```shell 
cargo build --release --features runtime-benchmarks
```

2. run benchmark test 
```shell 
./target/release/node-template benchmark --chain dev --execution=wasm --wasm-execution=compiled --pallet=pallet_template --extrinsic do_something --steps 2 --repeat 50
```

3. Generate chain-spec.json  
```shell 
./target/release/node-template build-spec > chain-spec-plain.json
./target/release/node-template build-spec --chain chain-spec-plain.json --raw --disable-default-bootnode > no-bootnodes-chain-spec-plain.json
./target/release/node-template build-spec --chain chain-spec-plain.json --raw > chain-spec.json
```

4. Launch local node  
```shell 
./target/release/node-template \
--base-path /tmp/node01 \
--chain ./chain-spec.json \
--port 30333 \
--ws-port 9945 \
--rpc-port 9933 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--rpc-methods Unsafe \
--name MyNode01
```


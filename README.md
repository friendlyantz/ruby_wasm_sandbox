RTFMing [ruby.wasm](https://github.com/ruby/ruby.wasm)

# 0 basic HTML + CDN

check index.html

# 1 basic ruby package

## download `wasmtime`

```sh
curl https://wasmtime.dev/install.sh -sSf | bash
```

## download the ruby.wasm release

```sh
# check releases, change the date in the URL
curl -LO https://github.com/ruby/ruby.wasm/releases/download/2024-04-17-a/ruby-3.3-wasm32-unknown-wasip1-full.tar.gz
tar xfz ruby-3.3-wasm32-unknown-wasip1-full.tar.gz
```

## create a simple ruby app

```sh
mkdir src
$ echo "puts 'Hello'" > src/my_app.rb
```

## ship it

```sh
rbwasm pack ruby.wasm --dir ./src::/src --dir ./ruby-3.3-wasm32-unknown-wasip1-full/usr::/usr -o my-ruby-app.wasm
```

## Run it

```sh
wasmtime my-ruby-app.wasm /src/my_app.rb
```

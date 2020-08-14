# ogx.token编译部署

## 依赖环境

1. eosio.cdt --- tag: v1.7.0 或以上
2. eosio.contract --- tag:  v1.9.1 或以上

## 编译

#### 1. 将ogx.token目录放入eosio.contracts内。
#### 2. 编辑文件 eosio.contracts/CMakeLists.txt:

```
add_subdirectory(ogx.token)
```
#### 3. 运行eosio.contracts/build.sh完成编译
 ```
 ./build.sh
 ```
 
 ## 部署
 
```
//创建帐号
cleos -u 'http://openapi.eos.ren' system newaccount --stake-net "0.1000 EOS" --stake-cpu "0.1000 EOS" --buy-ram-kbytes 6 tp organixtoken EOS77f1D5xApr9RaE7vS6ZDqWb9HteXhakoHgU6GZV6RzFu4tzTSR EOS77f1D5xApr9RaE7vS6ZDqWb9HteXhakoHgU6GZV6RzFu4tzTSR


cd build
cleos -u 'http://openapi.eos.ren' set contract organixtoken ./ogx.token -p organixtoken
```

## 创建代币
```
cleos -u 'https://eospush.tokenpocket.pro' push action organixtoken create '["organixtoken", "100000000.0000 OGX"]' -p organixtoken

cleos -u 'https://eospush.tokenpocket.pro' push action organixtoken issue '["organixtoken", "1.0000 OGX", "test"]' -p organixtoken
```
## 转账
```
cleos -u 'https://eospush.tokenpocket.pro' push action organixtoken transfer '["organixtoken", "b1", "0.0001 OGX", ""]' -p organixtoken
```
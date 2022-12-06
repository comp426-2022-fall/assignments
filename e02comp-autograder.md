# Comprehensive Final Exam Autograder config

This file includes all of the actual test scripts that the autograder action we are running for the comprehensive final exam.

## Run npm install

Setup command:
```

```

Run command:
```
npm install
```

This should run without an error.

## Check if the package license is set

Setup command:
```

```

Run command:
```
cat package.json
```

The license line should be changed to `GPL-3.0-or-later`

## Check for the author line

Setup command:
```

```

Run command:
```
cat package.json
```

Author line should be defined.

## Test 01.0

Setup command:
```

```

Run command:
```
PORT=5555; (timeout --signal=SIGINT 5 node ./01/server.js; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/ > test01-0.json && sleep 5s && if grep -q "It works!" test01-0.json; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 01.1

Setup command:
```

```

Run command:
```
PORT=5555; MESSAGE="$(openssl rand -hex 4)"; (timeout --signal=SIGINT 5 node ./01/server.js --port=${PORT} --message=${MESSAGE}; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/ > test01-1.json && sleep 5s && if grep -q ${MESSAGE} test01-1.json; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 02.0

Setup command:
```

```

Run command:
```
A="$(shuf -i 0-99 -n 1)"; B="$(shuf -i 0-99 -n 1)"; C="$(($A+$B))"; TEST=$(node --eval "const math = require('./02/math.js'); console.log(math.add(${A},${B}));"); if [ $C -eq $TEST ]; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 03.0

Setup command:
```

```

Run command:
```
PORT=5555; (timeout --signal=SIGINT 5 node ./03/server.js; exit 0) & sleep 1s && curl -s http://localhost:${PORT} > test03-0.html && sleep 5s && if grep -q "My server works." test03-0.html; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 03.1

Setup command:
```

```

Run command:
```
PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./03/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s http://localhost:${PORT} > test03-1.html && sleep 5s && if grep -q "My server works." test03-1.html; then echo "TRUE"; else echo "FALSE"; fi

```

Expected output if test passes: `TRUE`

## Test 04.0

Setup command:
```
npm install better-sqlite3 && npm install
```

Run command:
```
node --eval "const db = require('./04/database.js');"
```

Expected output if test passes: `TRUE`

## Test 04.1

Setup command:
```

```

Run command:
```
ls info.db
```

Expected output if test passes: `info.db`

## Test 04.2

Setup command:
```

```

Run command:
```
node --eval "const db = require('./04/database.js'); const customertab = db.prepare('SELECT * FROM customers').columns(); console.log(customertab);" > test04-1.txt && if grep -q "table: 'customers'," test04-1.txt; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 05.0

Setup command:
```

```

Run command:
```
LASTNAME="$(openssl rand -hex 4)"; FIRSTNAME="$(openssl rand -hex 4)"; EMAIL="$(openssl rand -hex 8)"; PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./05/server.js; exit 0) & sleep 1s && curl -s -X POST -d "lastname=${LASTNAME}&firstname=${FIRSTNAME}&email=${EMAIL}" http://localhost:5555/app/new/ && sleep 5s; (timeout --signal=SIGINT 5 node ./05/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s -X GET -d "email=${EMAIL}" http://localhost:${PORT}/app/lookup/ > test05-0.txt && sleep 5s && if grep -q "${LASTNAME}" test05-0.txt; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 06.0

Setup command:
```

```

Run command:
```
bash ./06/weather.sh
```

Expected output if test passes: `"radarStation": "KFCX"` in the JSON output.

## Test 07.0

Setup command:
```
cp ./07/weather.js ./07/weather.mjs
```

Run command:
```
node  ./07/weather.mjs --latitude=47.6062 --longitude=-122.3321
```

Expected output if test passes: `radarStation: 'KATX'` in the JSON output.

## Test 08.0

Setup command:
```

```

Run command:
```
PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./08/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/now/ > test08.json && sleep 5s && if grep -q "1670" test08.json; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 09.0

Setup command:
```

```

Run command:
```
PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./09/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/ && sleep 5s && wc -l ./09/access.log > test09.txt && if grep -q "[0-9]\{1,3\}\s" test09.txt; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

## Test 10.0

Setup command:
```

```

Run command:
```
A="$(shuf -i 0-99 -n 1)"; B="$(shuf -i 0-99 -n 1)"; C="$(($A+$B))"; PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./10/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/add/${A}/${B}/ > test10.txt && sleep 5s; if grep -q "${C}" test10.txt; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

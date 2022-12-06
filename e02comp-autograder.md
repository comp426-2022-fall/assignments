# Comprehensive Final Exam Autograder config

This file includes all of the actual test scripts that the autograder action we are running for the comprehensive final exam.

# Run npm install

Setup command:
```

```

Run command:
```
npm install
```



# Check if the package license is set

Setup command:
```

```

Run command:
```
cat package.json
```


# Check for the author line

Setup command:
```

```

Run command:
```
cat package.json
```

# Test 01.0

Setup command:
```

```

Run command:
```
PORT=5555; (timeout --signal=SIGINT 5 node ./01/server.js; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/ > test01-0.json && sleep 5s && if grep -q "It works!" test01-0.json; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

# Test 01.1

Setup command:
```

```

Run command:
```
PORT=5555; MESSAGE="$(openssl rand -hex 4)"; (timeout --signal=SIGINT 5 node ./01/server.js --port=${PORT} --message=${MESSAGE}; exit 0) & sleep 1s && curl -s http://localhost:${PORT}/app/ > test01-1.json && sleep 5s && if grep -q ${MESSAGE} test01-1.json; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

# Test 02.0

Setup command:
```

```

Run command:
```
A="$(shuf -i 0-99 -n 1)"; B="$(shuf -i 0-99 -n 1)"; C="$(($A+$B))"; TEST=$(node --eval "const math = require('./02/math.js'); console.log(math.add(${A},${B}));"); if [ $C -eq $TEST ]; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

# Test 03.0

Setup command:
```

```

Run command:
```
PORT=5555; (timeout --signal=SIGINT 5 node ./03/server.js; exit 0) & sleep 1s && curl -s http://localhost:${PORT} > test03-0.html && sleep 5s && if grep -q "My server works." test03-0.html; then echo "TRUE"; else echo "FALSE"; fi
```

Expected output if test passes: `TRUE`

# Test 03.1

Setup command:
```

```

Run command:
```
PORT=$(shuf -i 2000-65535 -n 1); (timeout --signal=SIGINT 5 node ./03/server.js --port=${PORT}; exit 0) & sleep 1s && curl -s http://localhost:${PORT} > test03-1.html && sleep 5s && if grep -q "My server works." test03-1.html; then echo "TRUE"; else echo "FALSE"; fi

```

Expected output if test passes: `TRUE`

# Test 04.0

Setup command:
```
npm install better-sqlite3 && npm install
```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`

# Test 01.0

Setup command:
```

```

Run command:
```

```

Expected output if test passes: `TRUE`


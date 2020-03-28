[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/badges/build.png?b=master)](https://scrutinizer-ci.com/g/sonrac/swagger-vue-doc-generator/build-status/master)

# Swagger vue documentation & api front generator

## Install

```bash
npm install --save-dev swagger-vue-generator
```

## Generate api:

Use script `node_modules/swagger-vue-generator/bin/generate-api.js`

### Arguments description

| Argument | Alias | Description | Notes |  
| -------- | ----- | ----------- | ----- |
| `-h` | `--help` | Show this help message and exit. | [optional] |
| `-v` | `--version` | Show this help message and exit. | [optional] |
| `-f` | `--flag-swagger` | Set swagger version (`2.0` or `openapi`). 2.0 only supported | [optional]. Default value is `2.0` |
| `-s` | `--source` | Source swagger file destination. | required |
| `-m` | `--moduleName` | Swagger generator module name. | required |
| `-c` | `--className` | Swagger generator class name. | [optional]. Default value is API |
| `-d` | `--destination` | Destination for output generate client. | required |

### Example usages

```bash
node ./node_modules/swagger-vue-generator/bin/generate-api.js -s /path/to/api-docs.json -d /path/to/api.js -m module-name 
```

## Generate README.MD for api

### Arguments description

| Argument | Alias | Description | Notes |  
| -------- | ----- | ----------- | ----- |
| `-h` | `--help` | Show this help message and exit. | [optional] |
| `-v` | `--version` | Show this help message and exit. | [optional] |
| `-s` | `--source` | Source swagger file destination. | required |
| `-f` | `--flag-swagger` | Set swagger version (`2.0` or `openapi`). 2.0 only supported | [optional]. Default value is `2.0` |
| `-m` | `--moduleName` | Swagger generator module name. | required |
| `-c` | `--className` | Swagger generator class name. | [optional]. Default value is API |
| `-t` | `--template` | Template dir. | [optional]. Default value is `./node_modules/swagger-vue-generator/src/2.0/templates/markdown` |
| `-d` | `--destination` | Destination for output generate client. | required |
|  | `--model-path` | Destination for models. | [optional] |
|  | `--doc-path` | Destination for methods. | [optional] |

### Custom templates

Change template path with option `-t` or `--template`.
Copy origin template from `./node_modules/swagger-vue-generator/src/2.0/templates/markdown` and change it

### Example usages

#### Generate doc
```
node ./node_modules/swagger-vue-generator/bin/generate-doc.js -s ../path/to/api-docs.json -d /path/to/destination -m module-name --model-path=models --doc-path=methods
```

#### Generate api
```
node ./node_modules/swagger-vue-generator/bin/generate-api.js -s ../path/to/api-docs.json -d /path/to/destination -m module-name
```

## Run tests

* Install dev dependencies

```bash
npm install --dev
```

* Run test
```bash
npm run test
```

## 修改
1. 文档产生优化
2. 不直接调用axios，而是调用自己的请求，方便自己在请求前处理或请求后处理，比如加token或者是返回状态判断
3. 如果请求参数在header里面，产生的api还有点问题???
4. 产生的doc文档，title不显示???

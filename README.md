# api-client
灵析 Api 通用 Client，基于 guzzlehttp/guzzle 实现

[![Build Status](https://travis-ci.org/LingxiTeam/api-client.svg?branch=master)](https://travis-ci.org/LingxiTeam/api-client)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/LingxiTeam/api-client/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/LingxiTeam/api-client/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/LingxiTeam/api-client/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/LingxiTeam/api-client/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/LingxiTeam/api-client/badges/build.png?b=master)](https://scrutinizer-ci.com/g/LingxiTeam/api-client/build-status/master)
### 安装

composer.json 中添加

```shell
composer require lingxi/api-client
```

### Feature
- 灵析 api 接口自动验证
- 支持接口参数自动替换。类似 Laravel 的路由参数替换。

### 用法

#### 初始化
> 全部参数都可以使用 Setter 方法设置。即不需要再实例化的时候传递参数。
```php
$apiOptions = [
    'base_uri'    => 'http://apixtest.lingxi360.com',
    'api_key'     => '5HQDDYDl1',
    'api_secret'  => 'NsqNx2Plv8eI1xwjr9QuCm6rl0nfThrk',
];
$apiClient = new ApiClient($apiOptions);
```
##### option 允许的值

|  选项  |  说明  |  默认值  |
| -----  |  -----  |  -----  |
|  `base_uri`      |  `base_uri`    |   Empty String    |
|  `time_out`      |  请求超时时间  |  `5.0`  |
|  `api_key`       |  `api_key`  |    Empty String   |
|  `api_secret`    |  `api_secret`    |   Empty String    |
|  `api_version`   |   Api 版本    |   'v1'    |

##### 链式操作
```php
$apiClient  = new ApiClient();
$apiClient->setBaseUri($apiOptions['base_uri'])
    ->setApiVersion($apiOptions['api_version'])
    ->setConsumer($apiOptions['api_key'], $apiOptions['api_secret'])
    ->setApiType($apiOptions['api_type'])
    ->setOutTime($apiOptions['time_out']);
```
#### 基本操作
```php
// 获取 Http 响应码
$apiClient->get($uri, $param)->getResponseCode();
// 获取 Http 响应对象。返回 GuzzleHttp\Psr7\Response 的实例
$apiClient->get($uri, $param)->getResponse();
// 获取 api 返回的数据
$apiClient->get($uri, $param)->getResponseData();
```
#### 获取最后一次请求的 URL
```php
$apiClient->getLastUrl();
$apiClient->getLastUrl();
```

#### Getter
```php
$apiClient->getBaseUri();
$apiClient->getApiVersion();
$apiClient->getOutTime();
$apiClient->getApiKey();
$apiClient->getApiSecret();
```
#### Setter
```php
$apiClient->setBaseUri();
$apiClient->setBaseUri();
$apiClient->setApiVersion();
$apiClient->setOutTime();
```
## License
MIT


The DM SDK for Aliyun OpenAPI
==============================

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]


The DM SDK for Aliyun OpenAPI

## Install

Via Composer

``` bash
$ composer require lokielse/aliyun-open-api-dm
```

## Usage

```php
/**
 * 访问信息
 */
$config = [
	'AccessKeyId'=>'<your access_key_id>',
	'AccessKeySecret'=>'<your access_key_secret>',
];

/**
 * 配置网关
 */
$endpoint = new Endpoint('cn-hangzhou', EndpointConfig::getRegionIds(), EndpointConfig::getProductDomains());
EndpointProvider::setEndpoints([ $endpoint ]);

/**
 * 授权资料
 */
$profile = DefaultProfile::getProfile('cn-hangzhou', $config['AccessKeyId'], $config['AccessKeySecret']);


/**
 * 请求对象
 */
$request = new SingleSendMailRequest();
$request->setAccountName('notice@push.example.com');
$request->setFromAlias('Pusher');
$request->setAddressType(1);
$request->setReplyToAddress('true');
$request->setToAddress('to@example.com');
$request->setSubject('Demo Subject');
$request->setHtmlBody('Hello World!');

$client  = new DefaultAcsClient($profile);
$response = $client->getAcsResponse($request);

var_dump($response);
```

[官方文档](https://help.aliyun.com/document_detail/29444.html)


## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email lokielse@gmail.com instead of using the issue tracker.

## Credits

- [Lokielse][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/lokielse/aliyun-open-api-dm.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/lokielse/aliyun-open-api-dm/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/lokielse/aliyun-open-api-dm.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/lokielse/aliyun-open-api-dm.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/lokielse/aliyun-open-api-dm.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/lokielse/aliyun-open-api-dm
[link-travis]: https://travis-ci.org/lokielse/aliyun-open-api-dm
[link-scrutinizer]: https://scrutinizer-ci.com/g/lokielse/aliyun-open-api-dm/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/lokielse/aliyun-open-api-dm
[link-downloads]: https://packagist.org/packages/lokielse/aliyun-open-api-dm
[link-author]: https://github.com/lokielse
[link-contributors]: ../../contributors
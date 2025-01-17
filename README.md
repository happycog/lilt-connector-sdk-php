# lilt-connector-sdk

This document describes the Plugin API for Lilt's Connector platform. The
Plugin API is intented to be used by developers who wish to build
integrations into their desired systems. The purpose of this API is to
enable content transfer and status monitoring for localization projects.

- Read more about the concepts and workflows in the
  [user guide](/docs/api/v1.0).
- Test the API interactively via [Swagger UI](/api/v1.0/ui).



## Installation & Usage

### Requirements

PHP 7.3 and later.
Should also work with PHP 8.0 or 8.1 but has not been tested.

### Composer

To install the bindings via [Composer](https://getcomposer.org/), add the following to `composer.json`:

```json
{
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/lilt/lilt-connector-sdk-php.git"
    }
  ],
  "require": {
    "lilt/lilt-connector-sdk-php": "*@dev"
  }
}
```

Then run `composer install`

### Manual Installation

Download the files and include `autoload.php`:

```php
<?php
require_once('/path/to/lilt-connector-sdk/vendor/autoload.php');
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



// Configure Bearer authorization: BearerAuth
$config = LiltConnectorSDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new LiltConnectorSDK\Api\JobsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 12345; // int | The Job ID.
$name = sample.txt; // string | The file name.
$srclang = 'en-US'; // string | The source language.
$trglang = array('trglang_example'); // string[] | The target language. Many target languages can be added to a source file.
$due = new \DateTime("2013-10-20T19:20:30+01:00"); // \DateTime | The due date for the file.
$body = "/path/to/file.txt"; // \SplFileObject

try {
    $apiInstance->servicesApiJobsAddFile($id, $name, $srclang, $trglang, $due, $body);
} catch (Exception $e) {
    echo 'Exception when calling JobsApi->servicesApiJobsAddFile: ', $e->getMessage(), PHP_EOL;
}

```

## API Endpoints

All URIs are relative to *https://connectors-admin.lilt.com/api/v1.0*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*JobsApi* | [**servicesApiJobsAddFile**](docs/Api/JobsApi.md#servicesapijobsaddfile) | **POST** /jobs/{id}/files | Add a file to a Job.
*JobsApi* | [**servicesApiJobsCreateJob**](docs/Api/JobsApi.md#servicesapijobscreatejob) | **POST** /jobs | Create a Connector Job.
*JobsApi* | [**servicesApiJobsGetJobById**](docs/Api/JobsApi.md#servicesapijobsgetjobbyid) | **GET** /jobs/{id} | Retrieve a Connector Job.
*JobsApi* | [**servicesApiJobsGetJobs**](docs/Api/JobsApi.md#servicesapijobsgetjobs) | **GET** /jobs | Retrieve a list of Connector Jobs.
*JobsApi* | [**servicesApiJobsStartJob**](docs/Api/JobsApi.md#servicesapijobsstartjob) | **POST** /jobs/{id}/start | Start a Job.
*JobsApi* | [**servicesApiJobsSyncJob**](docs/Api/JobsApi.md#servicesapijobssyncjob) | **POST** /jobs/{id}/sync | Start a Sync.
*RegistrationApi* | [**servicesApiRegistrationRegister**](docs/Api/RegistrationApi.md#servicesapiregistrationregister) | **POST** /register | Register a new connector installation.
*SettingsApi* | [**servicesApiSettingsGetSettings**](docs/Api/SettingsApi.md#servicesapisettingsgetsettings) | **GET** /settings | Retrieve the settings.
*SettingsApi* | [**servicesApiSettingsUpdateSettings**](docs/Api/SettingsApi.md#servicesapisettingsupdatesettings) | **PUT** /settings | Update the settings.
*TranslationsApi* | [**servicesApiDeliveriesDownloadDelivery**](docs/Api/TranslationsApi.md#servicesapideliveriesdownloaddelivery) | **GET** /translations/{id}/download | Download a Translation.
*TranslationsApi* | [**servicesApiDeliveriesGetDeliveriesByJobId**](docs/Api/TranslationsApi.md#servicesapideliveriesgetdeliveriesbyjobid) | **GET** /translations | Retrieve a list of Translations.
*TranslationsApi* | [**servicesApiDeliveriesGetDeliveryById**](docs/Api/TranslationsApi.md#servicesapideliveriesgetdeliverybyid) | **GET** /translations/{id} | Retrieve a Translation.

## Models

- [JobResponse](docs/Model/JobResponse.md)
- [JobResponse1](docs/Model/JobResponse1.md)
- [JobsResponse](docs/Model/JobsResponse.md)
- [RegistrationRequest](docs/Model/RegistrationRequest.md)
- [RegistrationResponse](docs/Model/RegistrationResponse.md)
- [SettingsResponse](docs/Model/SettingsResponse.md)
- [SettingsResponse1](docs/Model/SettingsResponse1.md)
- [TranslationResponse](docs/Model/TranslationResponse.md)

## Authorization

### BearerAuth

- **Type**: Bearer authentication

## Tests

To run the tests, use:

```bash
composer install
vendor/bin/phpunit
```

## Author



## About this package

This PHP package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: `1.0`
- Build package: `org.openapitools.codegen.languages.PhpClientCodegen`

<p align="center"><img src="https://raw.githubusercontent.com/zumcoin/zum-assets/master/ZumCoin/zumcoin_logo_design/3d_green_lite_bg/ZumLogo_800x200px_lite_bg.png" width="400"></p>

# ZUM Service PHP API Interface

This wrapper allows you to easily interact with the [ZUM Services](https://zum.services) 1.0.1 API to quickly develop applications that interact with the [ZumCoin](https://zumcoin.org) Network.


# Table of Contents

1. [Installation](#installation)
2. [Intialization](#intialization)
3. [Documentation](#documentation)
  1. [Methods](#methods)


# Installation

```bash
composer require zumcoin/zumservices-api-php
```


# Intialization

```php
use ZUMservices\ZUMservices;

$config = [
    'token' => 'eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoidGVzdCIsImFwcElkIjo0LCJ1c2VySWQiOjYsInBlcm1pc3Npb25zIjpbImFkZHJlc3M6bmV3Il0sImlhdCI6MTUzNjU4NTM2NywiZXhwIjoxNTM5MTc3MzY3LCJhdWQiOiJ0dXJ0bGV3YWxsZXQuaW8iLCJpc3MiOiJUUlRMIFNlcnZpY2VzIiwianRpIjoiMzMifQ.AEHXmvTo8RfNuZ15Y3IGPRhZPaJxFSmOZvVv2YGN9L4We7bXslIPxhMv_n_5cNW8sIgE2Fr-46OTb5H5AFgpjA',
    'timeout' => 2000
];

$ZS = new ZUMservices($config);

```

## Reponse Formattng

```php

// The result field from the RPC response
$response->result();

// RPC response as JSON string
$response->toJson();

// RPC response as an array
$response->toArray();
``` 


# Documentation

API documentation is available at https://zum.services/documentation


## Methods

### createAddress()
Create a new ZUM addresses

```php
$ZS->createAddress()
```


### getAddress(address)
Get address details by address
```php
$ZS->getAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### deleteAddress(address)
Delete a selected ZUM addresses

```php
$ZS->deleteAdddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### getAddresses()
View all addresses.

```php
$ZS->getAddresses()
```


### scanAddress(address, blockIndex)
Scan an address for transactions between a 100 block range starting from the specified blockIndex.

```php
$ZS->scanAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC", 899093)
```


### getAddressKeys(address)
Get the public and secret spend key of an address.

```php
$ZS->getAddressKeys("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### integrateAddress(address, paymentId)
Create an integrated address with an address and payment ID.

```php
$ZS->integrateAddress("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC", "7d89a2d16365a1198c46db5bbe1af03d2b503a06404f39496d1d94a0a46f8804")
```


### getIntegratedAddresses(address)
Get all integrated addresses by address.

```php
$ZS->getIntegratedAddresses("Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC")
```


### getFee(amount)
Calculate the ZUM Services fee for an amount specified in ZUM with two decimal points.

```php
$ZS->getFee(123.45)
```


### createTransfer(sender, receiver, amount, fee, paymentId, extra)
Send a ZUM transaction with an address with the amount specified two decimal points.

```php
$ZS->createTransfer(
  "Zum1yfSrdpfiSNG5CtYmckgpGe1FiAc9gLCEZxKq29puNCX92DUkFYFfEGKugPS6EhWaJXmhAzhePGs3jXvNgK4NbWXG4yaGBHC",
  "Zum1yhbRwHsXj19c1hZgFzgxVcWDywsJcDKURDud83MqMNKoDTvKEDf6k7BoHnfCiPbj4kY2arEmQTwiVmhoELPv3UKhjYjCMcm",
  1234.56,
  1.23,
  "7d89a2d16365a1198c46db5bbe1af03d2b503a06404f39496d1d94a0a46f8804",
  "3938f915a11582f62d93f82f710df9203a029f929fd2f915f2701d947f920f99"
)
```
#### You can leave the last two fields (paymentId and extra) blank.


### getTransfer(address)
Get a transaction details specified by transaction hash.

```php
$ZS->getTransfer("EohMUzR1DELyeQM9RVVwpmn5Y1DP0lh1b1ZpLQrfXQsgtvGHnDdJSG31nX2yESYZ")
```


### getWallet()
Get wallet container info and health check.

```php
$ZS->getWallet()
```


### getStatus()
Get the current status of the ZUM Services infrastructure.

```php
$ZS->getStatus()
```

# License

```
Copyright (C) 2019 ZumCoin Development Team

Please see the included LICENSE file for more information.
```

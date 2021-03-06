# Sofort. Disable notifications

When you are working locally with Sofort you may get 

```
<?xml version="1.0" encoding="UTF-8"?>
<errors>
  <error>
    <code>8016</code>
    <message>Must be a valid URL.</message>
    <field>notification_urls.notification_url.1</field>
  </error>
</errors>
```

That's because the notification url you sent to Sofort is not reachable and Sofort returns error in this case.
To work around the problem you can disable notifications by setting next option:

```php
<?php
namespace Acme;

use Payum\Sofort\SofortGatewayFactory;

$factory = new SofortGatewayFactory();

$gateway = $factory->create([
    'config_key' => 'aKey',
    'disable_notification' => true,
]);
```

and in Symfony:

```yaml
payum:
  gateways:
    sofort:
      config_key: 'aKey',
      disable_notification: true            
      facory: 'sofort'
```

Pay attention that you must do it only for local\dev environments and never in production.

Back to [index](../index.md).
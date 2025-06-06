---
title: Assert published times
weight: 5
---

Sometimes, you need to assert that Kafka has published a given number of messages. For that, you can use the `assertPublishedTimes` method:

```php
use PHPUnit\Framework\TestCase;
use Junges\Kafka\Facades\Kafka;
use Junges\Kafka\Message\Message;

class MyTest extends TestCase
{
    public function testWithSpecificTopic()
    {
        Kafka::fake();

        Kafka::publish('broker')
            ->onTopic('topic')
            ->withHeaders(['key' => 'value'])
            ->withBodyKey('key', 'value');

        Kafka::publish('broker')
            ->onTopic('topic')
            ->withHeaders(['key' => 'value'])
            ->withBodyKey('key', 'value');

        Kafka::assertPublishedTimes(2);
    }
} 
```

```+parse
<x-sponsors.request-sponsor/>
```
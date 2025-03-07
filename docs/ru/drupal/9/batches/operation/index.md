---
title: Обработка операции
slug: wiki/9/batches/operation
core: 9
metatags:
  title: 'Drupal 9: Обработка операции'
  description: 'Обработка пакетной операции в Drupal 9.'
category:
  area: Пакетная обработка
  title: Обработка операции
  order: 3
---

В процессе построения пакетной обработки вы задаете операции, которые необходимо обработать. Если вы используйте `BatchBuilder`, то это происходит при помощи метода `addOperation()`, где вы задаете функцию обратного вызова и данные на обработку.

В процессе выполнения пакетной обработки, будет произведен вызов каждой функции обратного вызова с данными переданными для неё. Каждая операция обрабатывается индивидуально.

В указанную вами функцию или метод в качестве аргументов будут переданные указанные вами данные, а самым последним, дополнительно, всегда передается аргумент `&$context`.

В массиве `$context` вы сможете найти следующую информацию:

- `results`: Массив с результатами работы операций. Обычно в данном массиве хранится то, какие элементы были обработаны.
- `sandbox`: Массив для хранения данных между итерациями и операциями.
- `finished`: Число от 0 до 1 отражающее степень завершенности выполнения текущей операции. Например 0.5 = 50%.
- `message`: При помощи данного параметра вы можете переопределить статусное сообщение для пользователя.

**Пример:**

```php
  public function processOperation($data, &$context) {
    // Do something with $data.

    $context['results']++;
  }
```

## Ссылки

- [Drupal 8: Batch API](https://niklan.net/blog/192), Niklan, 2018

# CacheAdapter
Адаптер механизма кеширования (в данном случае для BitrixFramework)

## Пример использования:
```php
$cache = new \travelsoft\CacheAdapter($id, $dir, $time);

// если актуального кеша нет, то производим вычисления (бизнес логика) в функции обратного вызова
// и возвращаем результат, который будет закеширован автоматически
if (empty($result = $cache->get())) {

  $result = $cache->caching(function () use ($cache) {
     
     // бизнес логика
     
     // добавляет тегированный кеш
     $cache->setTagCache({название тега});
     
     return $result;
    
  });
  
}
```

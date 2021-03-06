# Warm Meetings

Приложение "Теплые встречи" предназначено для организации встреч с друзьями.  
Доступны богатые социальные возможности, включая: подписки на события, комментарии, фотографии встреч, приватные события, уведомления на почту.

![](https://i.imgur.com/Blbv7JJ.png)

### Задействованные технологии

 - Деплой выполнен на VPS DigitalOcean, с использованием `Capistrano`.
  - Приложение работает под управлением `nginx` и `Phusion Passenger`. 
  - Для хранения данных используется СУБД `PostgreSQL`.  
  - Для рассылки почты используется сервис `Mailjet`, почта рассылается в фоновых задачах с помощью `Resque` и `Redis`. 
  - Фотографии встреч  и аватарки пользователей обрабатываются с помощью `carrierwave` и `rmagick`, загружаются на `Amazon AWS`.
- Реализована поддержка `OAuth2`, доступен вход с Facebook и VK.
- Авторизация организована с помощью `Pundit`.
- Локализация осуществлена с `i18n`.
- Интерфейс приложения выполнен с помощью `Bootstrap 4.6` с применением `JQuery`.

### Как установить 

Приложение написано с использованием `Rails 6.1.3`. Необходима версия `Ruby 2.7.2` и выше.

Для штатной установки `rmagick` необходимо установить его зависимости 

    $ sudo apt-get install libmagickwand-dev imagemagick
    
В проекте используется `bundler`, для установки зависимостей следует ввести

    $ bundle install

Приложению необходимы ключи для API AWS S3, yandex map, VK, FB и сервиса Mailjet.
Для нормальной работы необходимо дополнить следующие переменнные в `Rails credentials` своими данными.

AWS:
 - s3_bucket_name
 - s3_region
 - s3_secret_key
 - s3_access_key

 OAuth:
 - facebook_id
 - facebook_secret
 - vk_key
 - vk_id
 
 yandex
 - api_key

mailjet
 - api_key
 - secret_key
 - sender
 
 Для установки миграций

    $ bundle exec rails db:migrate

 Запуск осуществляется

    $ bundle exec rails s

 Приложение доступно по адресу `http://localhost:3000/`

##### Free License

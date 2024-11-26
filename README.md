# WireGuard / AmneziaWG Telegram Bot

Телеграм-бот на Python для управления [WireGuard](https://www.wireguard.com) / [AmneziaWG](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module). Этот бот позволяет легко управлять клиентами. Подразумевается, что у вас уже установлен Python 3.11.x (на 3.12.x возникают ошибки). Используется библиотека `aiogram` версии 2.25.2.

## Оглавление

- [Возможности](#возможности)
- [Установка](#установка)
- [Запуск](#запуск)
- [Заметки](#заметки)
- [Поддержка](#поддержка)

## Возможности

- Добавление клиентов
- Удаление клиентов
- Блокировка/разблокировка клиентов
- Создание временных конфигураций (1 час, 1 день, 1 неделя, 1 месяц, неограниченно)
- Получение информации об IP-адресе клиента (берется из Endpoint, используется API ресурса [ip-api.com](http://ip-api.com))
- Создание ключа в формате `vpn://` при генерации нового клиента (так же, при получении конфигурации клиента), для использования в [AmneziaVPN](https://github.com/amnezia-vpn/amnezia-client)
- Создание резервной копии

## Установка

1. Установите [WireGuard](https://www.wireguard.com) или [AmneziaWG](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module) (без данного шага бот РАБОТАТЬ НЕ БУДЕТ).

2. Создайте бота в Telegram:

- Откройте Telegram и найдите бота [BotFather](https://t.me/BotFather).
- Начните диалог, отправив команду `/start`.
- Введите команду `/newbot`, чтобы создать нового бота.
- Следуйте инструкциям BotFather, чтобы:
    - Придумать имя для вашего бота (например, `WireGuardManagerBot`).
    - Придумать уникальное имя пользователя для бота (например, `WireGuardManagerBot_bot`). Оно должно оканчиваться на `_bot`.
- После создания бота BotFather отправит вам токен для доступа к API. Его запросит бот во время первоначальной инициализации.

3. Загрузите и запустите скрипт `install.sh`, с помощью которого будет автоматически установлен бот, со всеми зависимостями, в том числе, в качестве системной службы (автозапуск):

    ```bash
    curl -O https://raw.githubusercontent.com/JB-SelfCompany/awg_bot/main/install.sh && chmod +x install.sh && ./install.sh
    ```

## Запуск
    
1. Добавьте бота в Telegram и отправьте команду `/start` или `/help` для начала работы.

## Заметки

При создании резервной копии, в архив добавляется директория connections (создается и содержит в себе логи подключений клиентов), conf, png, и сам конфигурационный файл. 

Вы можете дополнительно воспользоваться скриптом для генерации конфигурации, для [WireGuard](https://www.wireguard.com) или [AmneziaWG](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module), если желаете добавить отдельные подсети/интерфейсы/конфигурационные файлы:

    ./genconf.sh
    
**Важно:** Для корректной работы требуется запуск бота от имени пользователя с правами `sudo`, если [WireGuard](https://www.wireguard.com) / [AmneziaWG](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module) настроен с повышенными привилегиями. [WireGuard](https://www.wireguard.com) / [AmneziaWG](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module) должен быть настроен и запущен на сервере до использования бота.

## Поддержка

Если у вас возникли вопросы или проблемы с установкой и использованием бота, создайте [issue](https://github.com/JB-SelfCompany/awg_bot/issues) в этом репозитории или обратитесь к разработчику.

- [Matrix](https://matrix.to/#/@jack_benq:shd.company)

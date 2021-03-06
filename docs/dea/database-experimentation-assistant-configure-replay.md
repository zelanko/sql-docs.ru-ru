---
title: Настройка воспроизведения для SQL Server обновлений
description: Используйте Database Experimentation Assistant (ДЕА) для доступа к средствам распределенное воспроизведение. Используйте средства для воспроизведения захваченной трассировки в обновленной тестовой среде.
ms.custom: seo-lt-2019
ms.date: 01/24/2020
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pochiraju
ms.author: rajpo
ms.reviewer: mathoma
ms.openlocfilehash: 7001f188b00e70c2616e8c3592d7fa9e34147321
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419789"
---
# <a name="configure-distributed-replay-for-database-experimentation-assistant"></a>Настройка распределенное воспроизведение для Database Experimentation Assistant

Database Experimentation Assistant (ДЕА) использует средства распределенное воспроизведение из установки SQL Server для воспроизведения захваченной трассировки в обновленной тестовой среде. Рекомендуется выполнить тестовый запуск, используя небольшой файл трассировки перед выполнением полного воспроизведения, чтобы обеспечить правильное воспроизведение запросов.

## <a name="distributed-replay-requirements"></a>Требования распределенного воспроизведения

- Для создания файлов ИРФ на компьютере контроллера распределенное воспроизведение требуется дополнительно 78% свободного пространства на жестком диске.
- 200 МБ или 512 МБ — идеальный размер переключения трассировки, используемый для сбора данных трассировки производства или производительности.
- Минимальные требования к ЦП и ОЗУ для контроллера распределенное воспроизведение и клиентских компьютеров — это одноядерный ЦП с 3,5 ГБ ОЗУ.
- Время воспроизведения занимает примерно 1,55 раз дольше, чем время записи, так как один контроллер и четыре дочерних компьютера используются для воспроизведения производственной трассировки.
- При использовании наших опубликованных версий файлов определения трассировки производительности и определения трассировки производительности фильтрует трассировку одной базы данных, которая представляет интерес, анализ показывает, что размер **трассировки производительности** составляет примерно 15 раз больше, чем размер **трассировки рабочей среды** .

## <a name="set-up-a-virtual-network-or-domain"></a>Настройка виртуальной сети или домена

Для распределенное воспроизведение требуется использовать общие учетные записи между компьютерами. Из-за этого требования и по соображениям безопасности рекомендуется запускать распределенное воспроизведение в виртуальной сети или в сети, находящихся под управлением домена:

- Создайте в среде контроллер и клиентские компьютеры.
- Убедитесь, что контроллер и клиентские компьютеры могут проверить связь друг с другом по сети.
- Распределенное воспроизведение клиентские компьютеры должны иметь подключение к конечному компьютеру воспроизведения, на котором работает SQL Server.

## <a name="set-up-the-controller-service"></a>Настройка службы контроллера

Чтобы настроить службу контроллера, выполните следующие действия.

1. Установите контроллер распределенное воспроизведение с помощью установщика SQL Server. Если вы пропустили шаг мастера установки SQL Server, который настраивает контроллер распределенное воспроизведение, можно настроить контроллер с помощью файла конфигурации. В типичной установке файл конфигурации находится в папке C:\Program Files (x86) \Microsoft SQL Server \<version\>\Tools\DReplayController\DReplayController.config.
2. Журналы распределенное воспроизведение контроллеров расположены в папке C:\Program Files (x86) \Microsoft SQL Server \<version\> \тулс\дреплайконтроллер\лог.
3. Откройте Services. msc и перейдите к службе **контроллера распределенное воспроизведение SQL Server** .
4. Щелкните службу правой кнопкой мыши и выберите пункт **Свойства**. Задайте учетной записи службы учетную запись, общую для контроллера и клиентских компьютеров в сети.
5. Нажмите кнопку **ОК** , чтобы закрыть окно **свойства** .
6. Перезапустите службу **контроллера распределенное воспроизведение SQL Server** из Services. msc. Для перезапуска службы можно также выполнить следующие команды в командной строке:

   `NET STOP "SQL Server Distributed Replay Controller"`</br>
   `NET START "SQL Server Distributed Replay Controller"`

Дополнительные параметры конфигурации см. в разделе [Configure распределенное воспроизведение](../tools/distributed-replay/configure-distributed-replay.md).

## <a name="configure-dcom"></a>Настройка DCOM

Эта конфигурация требуется только на компьютере контроллера.

1. Откройте dcomcnfg.exe.
2. Разверните узел **службы компонентов**  >  **Компьютеры**  >  **Мой компьютер**  >  **конфигурацию DCOM**.
3. В разделе **конфигурация DCOM** щелкните правой кнопкой мыши **DReplayController** и выберите пункт **Свойства**.
4. Перейдите на вкладку **Безопасность**.
5. В разделе **разрешения на запуск и активацию** выберите **Настройка**, а затем щелкните **изменить**.
6. Добавьте пользователя, который будет запускать воспроизведение. Предоставьте локальным пользователям разрешения на запуск и локальную активацию. Если пользователь планирует запустить или активировать удаленно, предоставьте пользователю разрешения на удаленный запуск и удаленную активацию.
7. Нажмите кнопку **ОК** , чтобы зафиксировать изменения и вернуться на вкладку **Безопасность** .
8. В разделе **разрешения на доступ** выберите **Настройка**, а затем щелкните **изменить**.
9. Добавьте пользователя, который будет запускать воспроизведение. Предоставьте пользователю права локального доступа. Если пользователь планирует удаленно получить доступ к службе контроллера, предоставьте пользователю разрешения на удаленный доступ.
10. Нажмите кнопку **ОК** , чтобы зафиксировать изменения и вернуться на вкладку **Безопасность** .
11. Нажмите кнопку **ОК** , чтобы зафиксировать изменения.
12. Перезапустите службу контроллера распределенное воспроизведение SQL Server из Services. msc. Для перезапуска службы можно также выполнить следующие команды в командной строке:

    `NET STOP "SQL Server Distributed Replay Controller"`</br>
    `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>Настройка службы клиента

Перед настройкой службы клиента используйте такие средства работы с сетью, как проверка связи, чтобы убедиться, что контроллер и клиентские компьютеры могут обмениваться данными.

1. Установите клиент распределенное воспроизведение с помощью установщика SQL Server.
2. Откройте Services. msc и перейдите в службу клиента SQL Server распределенное воспроизведение.
3. Щелкните службу правой кнопкой мыши и выберите пункт **Свойства**. Задайте учетной записи службы учетную запись, общую для контроллеров и клиентских компьютеров в сети.
4. Нажмите кнопку **ОК** , чтобы закрыть окно **свойства** . Если вы пропустили шаг мастера установки SQL Server для настройки клиента распределенное воспроизведение, его можно настроить с помощью файла конфигурации. В типичной установке файл конфигурации находится в папке C:\Program Files (x86) \Microsoft SQL Server \<version\>\Tools\DReplayClient\DReplayClient.config.
5. Убедитесь, что файл DReplayClient.config содержит имя компьютера контроллера в качестве контроллера для регистрации.
6. Перезапустите службу клиента SQL Server распределенное воспроизведение из Services. msc. Для перезапуска службы можно также выполнить следующие команды из командной строки:

    `NET STOP "SQL Server Distributed Replay Client"`</br>
    `NET START "SQL Server Distributed Replay Client"`

    Журналы распределенное воспроизведение контроллеров расположены в папке C:\Program Files (x86) \Microsoft SQL Server \<version\> \тулс\дреплайклиент\лог. Журналы указывают, может ли клиент зарегистрироваться в контроллере.

    Если конфигурация прошла успешно, в журнале отображается сообщение, **зарегистрированное с помощью имени \> контроллера <контроллера**.

Дополнительные параметры конфигурации см. в разделе [Configure распределенное воспроизведение](../tools/distributed-replay/configure-distributed-replay.md).

## <a name="set-up-distributed-replay-administration-tools"></a>Настройка средств администрирования распределенное воспроизведение

С помощью средств администрирования распределенное воспроизведение можно быстро проверить, правильно ли работает распределенное воспроизведение в среде. Тестирование конфигурации может быть особенно полезным в среде, в которой несколько клиентских компьютеров зарегистрированы в контроллере. Чтобы получить средства администрирования, может потребоваться установить SQL Server Management Studio (SSMS).

1. Перейдите в каталог установки SSMS и найдите средство администрирования распределенное воспроизведение dreplay.exe и зависимые компоненты. В настоящее время [SSMS 17](../ssms/release-notes-ssms.md#1791) — это последний выпуск SSMS для включения dreplay.exe.
2. В командной строке выполните команду `dreplay.exe status -f 1` .

Если предыдущие шаги были успешными, выходные данные консоли указывают на то, что контроллер может видеть клиентов в `READY` состоянии.

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Настройка брандмауэра для удаленного доступа к распределенное воспроизведение

Для удаленного доступа к распределенное воспроизведение требуются открытые порты, видимые в пределах домена или виртуальной сети.

1. Откройте **Брандмауэр Windows** в **расширенной безопасности**.
2. Перейдите к **правилам для входящих подключений**.
3. Создайте новое правило для входящего трафика брандмауэра для программы C:\Program Files (x86) \Microsoft SQL Server \<version\>\Tools\DReplayController\DReplayController.exe.
4. Разрешите доступ на уровне домена ко всем портам, чтобы DReplayController.exe могли удаленно взаимодействовать со службой контроллера.
5. Сохраните правило.

## <a name="set-up-target-computers"></a>Настройка целевых компьютеров

Для выполнения теста A/B или эксперимента требуются два воспроизведения. То есть для сценария миграции могут потребоваться два отдельных экземпляра SQL Server установки.

Можно также установить две версии SQL Server экземпляров на одном компьютере. Для этого необходимо убедиться, что экземпляры изолированы, когда выполняется воспроизведение.

Для каждого воспроизведения необходимо выполнить следующие действия.

1. Восстановите резервную копию базы данных.
2. Предоставьте пользователям учетной записи службы клиента разрешения на доступ к базам данных в экземпляре SQL Server. Для выполнения запросов на экземпляре SQL Server необходимы разрешения.
3. Запустите воспроизведение.

## <a name="see-also"></a>См. также

- Сведения о воспроизведении захваченной трассировки в обновленной тестовой среде см. в разделе [Воспроизведение трассировки в Database experimentation Assistant](database-experimentation-assistant-replay-trace.md).

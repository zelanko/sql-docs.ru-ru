---
title: "Справочник по ошибкам и событиям (репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [SQL Server replication], troubleshooting
- troubleshooting [SQL Server replication], errors
- replication [SQL Server], troubleshooting
- errors [SQL Server replication]
- errors and events reference [SQL Server replication]
ms.assetid: e67d1bab-47b6-441d-ab9c-251a2ca499e1
caps.latest.revision: "25"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a053348a203ad7d1e3a9a3cf9fa0f7672300b64
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="errors-and-events-reference-replication"></a>Справочник по ошибкам и событиям (репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Этот раздел документации содержит информацию о причинах и способах устранения ошибок, связанных с репликацией.  
  
|Ошибка|Сообщение|  
|-----------|-------------|  
|[MSSQL_ENG002601](../../relational-databases/replication/mssql-eng002601.md)|Не удается вставить повторяющуюся строку ключа в объект "%.*ls" с уникальным индексом "%.\*ls".|  
|[MSSQL_ENG002627](../../relational-databases/replication/mssql-eng002627.md)|Нарушение ограничения "%.*ls" для %ls. Не удается вставить повторяющийся ключ в объект "%.\*ls".|  
|[MSSQL_ENG003165](../../relational-databases/replication/mssql-eng003165.md)|База данных "%ls" была восстановлена, однако во время восстановления или удаления репликации обнаружена ошибка. База данных находится в режиме «вне сети». См. раздел MSSQL_ENG003165 в электронной документации по SQL Server.|  
|[MSSQL_ENG003724](../../relational-databases/replication/mssql-eng003724.md)|Невозможно %S_MSG %S_MSG "%.*ls", так как она используется для репликации.|  
|[MSSQL_ENG004929](../../relational-databases/replication/mssql-eng004929.md)|Невозможно изменить %S_MSG "%.*ls", так как выполняется публикация для репликации.|  
|MSSQL_ENG007395. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Невозможно запустить вложенную транзакцию для поставщика OLE DB "%ls" для связанного сервера "%ls". Вложенная транзакция потребовалась из-за того, что параметр XACT_ABORT был установлен в OFF.|  
|[MSSQL_ENG014005](../../relational-databases/replication/mssql-eng014005.md)|Не удалось удалить публикацию. На нее существует подписка.|  
|[MSSQL_ENG014010](../../relational-databases/replication/mssql-eng014010.md)|Сервер "%s" не определен как сервер подписок.|  
|[MSSQL_ENG014114](../../relational-databases/replication/mssql-eng014114.md)|'%s' не настроен в качестве распространителя.|  
|[MSSQL_ENG014117](../../relational-databases/replication/mssql-eng014117.md)|"%s" не настроена в качестве базы данных распространителя.|  
|[MSSQL_ENG014120](../../relational-databases/replication/mssql-eng014120.md)|Не удается удалить базу данных "%s" распространителя. Эта база данных распространителя связана с издателем.|  
|[MSSQL_ENG014121](../../relational-databases/replication/mssql-eng014121.md)|Не удалось удалить распространитель "%s". С этим распространителем связаны базы данных распространителя.|  
|[MSSQL_ENG014144](../../relational-databases/replication/mssql-eng014144.md)|Невозможно удалить подписчик '%s'. В базе данных публикации '%s' для него есть подписки.|  
|[MSSQL_ENG014150](../../relational-databases/replication/mssql-eng014150.md)|Репликация-%s: агент %s выполнен успешно. %s|  
|[MSSQL_ENG014151](../../relational-databases/replication/mssql-eng014151.md)|Репликация-%s: ошибка агента %s. %s|  
|[MSSQL_ENG014152](../../relational-databases/replication/mssql-eng014152.md)|Репликация-%s: назначено повторное выполнение агента %s. %s|  
|[MSSQL_ENG014157](../../relational-databases/replication/mssql-eng014157.md)|Подписка, созданная подписчиком "%s" на издателе "%s", истекла и была удалена.|  
|[MSSQL_ENG014160](../../relational-databases/replication/mssql-eng014160.md)|Задан порог [%s:%s] для публикации [%s]. Срок действия подписки на эту публикацию истек у одного или нескольких подписчиков.|  
|[MSSQL_ENG014161](../../relational-databases/replication/mssql-eng014161.md)|Задан порог [%s:%s] для публикации [%s]. Убедитесь, что агент чтения журналов и агент распространителя запущены и соответствуют требованию по задержке.|  
|[MSSQL_ENG014162](../../relational-databases/replication/mssql-eng014162.md)|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
|[MSSQL_ENG014163](../../relational-databases/replication/mssql-eng014163.md)|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
|[MSSQL_ENG014164](../../relational-databases/replication/mssql-eng014164.md)|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
|[MSSQL_ENG014165](../../relational-databases/replication/mssql-eng014165.md)|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
|[MSSQL_ENG018456](../../relational-databases/replication/mssql-eng018456.md)|Ошибка входа пользователя '%.*ls'.%.\*ls|  
|[MSSQL_ENG018752](../../relational-databases/replication/mssql-eng018752.md)|К базе данных одновременно может быть подключен лишь один агент чтения журнала или процедура, относящаяся к журналу (sp_repldone, sp_replcmds и sp_replshowcmds). Если выполняется процедура, относящаяся к журналу, удалите подключение, по которому выполнялась процедура, или выполните для этого подключения процедуру sp_replflush, прежде чем запустить агент чтения журнала или выполнить другую процедуру, относящуюся к журналу.|  
|[MSSQL_ENG020554](../../relational-databases/replication/mssql-eng020554.md)|Агент репликации не зарегистрировал сообщение о ходе выполнения в течение %ld минут. Это может указывать на то, что агент не отвечает, либо на высокую загрузку системы. Убедитесь, что записи реплицируются по назначению, а подключения к подписчику, издателю и распространителю все еще активны.|  
|[MSSQL_ENG020557](../../relational-databases/replication/mssql-eng020557.md)|Завершение работы агента. Дополнительные сведения см. в журнале заданий агента SQL Server для задания «%s».|  
|[MSSQL_ENG020572](../../relational-databases/replication/mssql-eng020572.md)|Подписка подписчика "%s" на статью "%s" в публикации "%s" повторно инициализирована после ошибки при проверке.|  
|[MSSQL_ENG020574](../../relational-databases/replication/mssql-eng020574.md)|Ошибка проверки данных подписки подписчика "%s" на статью "%s" в публикации "%s".|  
|[MSSQL_ENG020575](../../relational-databases/replication/mssql-eng020575.md)|Подписка подписчика "%s" на статью "%s" в публикации "%s" прошла проверку данных.|  
|[MSSQL_ENG020596](../../relational-databases/replication/mssql-eng020596.md)|Только '%s' или члены роли db_owner могут удалить анонимный агент.|  
|[MSSQL_ENG020598](../../relational-databases/replication/mssql-eng020598.md)|При применении реплицированной команды строка на подписчике не была найдена.|  
|[MSSQL_ENG021075](../../relational-databases/replication/mssql-eng021075.md)|Исходный моментальный снимок публикации "%s" еще недоступен.|  
|[MSSQL_ENG021076](../../relational-databases/replication/mssql-eng021076.md)|Исходный моментальный снимок для статьи "%s" еще не доступен.|  
|[MSSQL_ENG021286](../../relational-databases/replication/mssql-eng021286.md)|Таблица конфликтов "%s" не существует.|  
|[MSSQL_ENG021330](../../relational-databases/replication/mssql-eng021330.md)|Не удалось создать вложенный каталог в рабочем каталоге репликации.(%ls)|  
|[MSSQL_ENG021331](../../relational-databases/replication/mssql-eng021331.md)|Не удалось скопировать файл пользовательского скрипта на распространитель.(%ls)|  
|[MSSQL_ENG021385](../../relational-databases/replication/mssql-eng021385.md)|Не удалось создать моментальный снимок для публикации "%s". Возможно, из-за изменений в схеме или из-за статей, добавленных во время создания снимка.|  
|MSSQL_ENG021617. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Невозможно запустить SQL*PLUS. Убедитесь, что текущая версия клиентской программы доступа к Oracle установлена у распространителя.|  
|MSSQL_ENG021620. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Версия SQL*PLUS, доступная через переменную системного пути, недостаточно актуальна для поддержания публикации Oracle. Убедитесь, что текущая версия клиентской программы доступа к Oracle установлена у распространителя.|  
|MSSQL_ENG021624. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Не найден зарегистрированный поставщик OLEDB для Oracle (OraOLEDB.Oracle) на распространителе "%s". Убедитесь, что текущая версия поставщика OLEDB для Oracle установлена и зарегистрирована на распространителе.|  
|MSSQL_ENG021626. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Не удается подключиться к серверу "%s" базы данных Oracle, используя зарегистрированный поставщик OLEDB для Oracle (OraOLEDB.Oracle).|  
|MSSQL_ENG021627. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Невозможно связаться с сервером '%s' базы данных Oracle, используя поставщик Microsoft OLEDB (MSDAORA).|  
|MSSQL_ENG021628. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Невозможно обновить реестр распространителя '%s', чтобы позволить поставщику OLEDB для Oracle(OraOLEDB.Oracle) запустить процесс с SQL Server. Убедитесь, что текущей учетной записи разрешено вносить изменения в разделы системного реестра SQL Server.|  
|MSSQL_ENG021629. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Раздел реестра CLSID, указывающий, что поставщик OLEDB для Oracle (OraOLEDB.Oracle) был зарегистрирован, но отсутствует на распространителе. Убедитесь, что поставщик OLEDB для Oracle установлен и зарегистрирован на распространителе.|  
|MSSQL_ENG021642. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Для разнородных издателей требуется использовать связанный сервер. Связанный сервер с именем "%s" уже существует. Удалите связанный сервер или выберите иное название издателя.|  
|MSSQL_ENG021663. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Не найден правильный первичный ключ для исходной таблицы [%s]. [%s].|  
|MSSQL_ENG021684. См. раздел [Troubleshooting Oracle Publishers](../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).|Разрешений, связанных с именем входа администратора для издателя Oracle «%s», недостаточно.|  
|[MSSQL_ENG021797](../../relational-databases/replication/mssql-eng021797.md)|"%s" должно быть допустимым именем входа Windows, представленным в следующем виде: "КОМПЬЮТЕР\имя_входа" или "ДОМЕН\имя_входа". См. документацию по "%s".»|  
|[MSSQL_ENG021798](../../relational-databases/replication/mssql-eng021798.md)|«Перед тем как продолжить, необходимо добавить задание агента "%s" через "%s". См. документацию по "%s".»|  
|[MSSQL_REPL020011](../../relational-databases/replication/mssql-repl020011.md)|Процессу не удалось выполнить '%1' на '%2'.|  
|[MSSQL_REPL027056](../../relational-databases/replication/mssql-repl027056.md)|Процессу слияния не удалось изменить журнал поколений в '%1'. В целях диагностики запустите синхронизацию повторно, включив подробное протоколирование и укажите выходной файл для записи.|  
|[MSSQL_REPL027183](../../relational-databases/replication/mssql-repl027183.md)|Процессу слияния не удалось перечислить изменения в статьях с параметризованными фильтрами строк. Если эта ошибка продолжает возникать, увеличьте тайм-аут запроса для этого процесса, уменьшите срок хранения публикации и оптимизируйте индексы по опубликованным таблицам.|  
  
  

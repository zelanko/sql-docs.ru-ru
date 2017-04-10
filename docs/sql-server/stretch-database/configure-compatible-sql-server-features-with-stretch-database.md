---
title: "Настройка совместимых функций SQL Server для работы с Базой данных Stretch | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8121ede-1aec-459b-b7b0-1408bb3e62fb
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 4
---
# Настройка совместимых функций SQL Server для работы с Базой данных Stretch
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Настройте указанные ниже компоненты SQL Server для работы с Базой данных Stretch с помощью простых действий.
-   AlwaysOn
-   Постоянное шифрование
-   Прозрачное шифрование данных (TDE)
-   Темпоральные таблицы

## Настройка AlwaysOn для работы с Базой данных Stretch
Если вы используете AlwaysOn с Базой данных Stretch, необходимо убедиться, что главный ключ базы данных доступен на вторичных репликах. База данных Stretch использует главный ключ базы данных для защиты учетных данных, используемых для подключения к удаленной базе данных Azure.

После настройки группы доступности AlwaysOn запустите хранимую процедуру **sp_control_dbmasterkey_password** во вторичной реплике и укажите пароль для базы данных с поддержкой Stretch. Дополнительные сведения и примеры см. в разделе [sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md). 

## Настройка Always Encrypted для работы с Базой данных Stretch
Для совместного использования Always Encrypted и Базы данных Stretch необходимо настроить шифрование выбранных столбцов, прежде чем включить Базу данных Stretch для таблицы.

Если вы уже включили Базу данных Stretch для таблицы и хотите использовать столбцы Always Encrypted, необходимо сделать следующее.
1.   Отключите Базу данных Stretch для таблицы и возвратите удаленные данные из Azure. Дополнительные сведения см. в разделе [Отключение базы данных Stretch и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).
2.   Настройте Always Encrypted для выбранных столбцов.
3. Повторно включите Базу данных Stretch для таблицы. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).

## Настройка прозрачного шифрования данных (TDE) для работы с Базой данных Stretch

Если TDE включено для локальной базы данных, оно не будет автоматически включено для удаленной конечной точки Базы данных Stretch. Необходимо не забыть включить TDE на удаленной конечной точке после включения функции Stretch для базы данных.

## Настройка темпоральных таблиц для работы с Базой данных Stretch
При использовании темпоральных таблиц Базу данных Stretch можно включить для таблицы журнала, но не для текущей таблицы.
-   Рекомендации по использованию темпоральных таблиц вместе с Базой данных Stretch см. в разделе [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).
-   Сведения о фильтрации переносимых строк из таблицы журнала с помощью скользящего окна см. в разделе [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).
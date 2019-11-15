---
title: Настройка совместимых функций SQL Server
ms.date: 03/14/2017
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c8121ede-1aec-459b-b7b0-1408bb3e62fb
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: d558dad38492bcd9ce2bad0eb00a887a2225de33
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844568"
---
# <a name="configure-compatible-sql-server-features-with-stretch-database"></a>Настройка совместимых функций SQL Server для работы с Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


Настройте указанные ниже компоненты SQL Server для работы с Stretch Database с помощью простых действий.
-   AlwaysOn
-   Always Encrypted
-   Прозрачное шифрование данных (TDE)
-   Темпоральные таблицы

## <a name="configure-always-on-with-stretch-database"></a>Настройка AlwaysOn для работы с Stretch Database
Если вы используете AlwaysOn с Stretch Database, необходимо убедиться, что главный ключ базы данных доступен на вторичных репликах. Stretch Database использует главный ключ базы данных для защиты учетных данных, используемых для подключения к удаленной базе данных Azure.

После настройки группы доступности AlwaysOn запустите хранимую процедуру **sp_control_dbmasterkey_password** во вторичной реплике и укажите пароль для базы данных с поддержкой Stretch. Дополнительные сведения и примеры см. в разделе [sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md). 

## <a name="configure-always-encrypted-with-stretch-database"></a>Настройка Always Encrypted для работы с Stretch Database
Для совместного использования Always Encrypted и Stretch Database необходимо настроить шифрование выбранных столбцов, прежде чем включить Stretch Database для таблицы.

Если вы уже включили Stretch Database для таблицы и хотите использовать столбцы Always Encrypted, необходимо сделать следующее.
1.   Отключите Stretch Database для таблицы и верните удаленные данные из Azure. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).
2.   Настройте Always Encrypted для выбранных столбцов.
3. Повторно включите Stretch Database для таблицы. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).

## <a name="configure-transparent-data-encryption-tde-with-stretch-database"></a>Настройка прозрачного шифрования данных (TDE) для работы с Stretch Database

Если TDE включено для локальной базы данных, оно не будет автоматически включено для удаленной конечной точки Базы данных Stretch. Необходимо не забыть включить TDE на удаленной конечной точке после включения функции Stretch для базы данных.

## <a name="configure-temporal-tables-with-stretch-database"></a>Настройка темпоральных таблиц для работы с Stretch Database
При использовании темпоральных таблиц Stretch Database можно включить для таблицы журнала, но не для текущей таблицы.
-   Рекомендации по использованию темпоральных таблиц вместе с Stretch Database см. в разделе [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).
-   Сведения о фильтрации переносимых строк из таблицы журнала с помощью скользящего окна см. в разделе [Выбор строк для миграции с использованием функции фильтров](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).
-   Вы не можете включить базу данных Stretch Database для темпоральной таблицы журнала, если эта таблица является оптимизированной для памяти. Таблицы, оптимизированные для памяти, не поддерживаются.

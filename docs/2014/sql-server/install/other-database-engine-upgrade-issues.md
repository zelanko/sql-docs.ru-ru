---
title: Другие проблемы обновления Database Engine | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f247f9addde6baa949f3260d7a9d9f86ce0c5bff
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093702"
---
# <a name="other-database-engine-upgrade-issues"></a>Другие проблемы обновления компонента Database Engine
  Текущая версия помощника по обновлению не может обнаружить следующие проблемы, возникающие при обновлении. Ознакомьтесь с нижеприведенным списком проблем, чтобы оценить потенциальные последствия для систем.  
  
## <a name="multiple-database-engine-deprecated-features"></a>Некоторые устаревшие функции компонента Database Engine  
 Следующие инструкции или параметры [!INCLUDE[tsql](../../includes/tsql-md.md)] устарели.  
  
-   параметры NO_LOG и TRUNCATE_ONLY инструкции BACKUP LOG;  
  
-   BACKUP TRANSACTION;  
  
-   RESTORE TRANSACTION;  
  
-   DUMP;  
  
-   LOAD  
  
-   DBCC CONCURRENCYVIOLATION  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
-   syssegments  
  
 Использование протокола VIA для подключения к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] устарело.  
  
## <a name="new-data-types"></a>Новые типы данных  
 Следующие типы данных будут зарезервированными системными типами. Перед обновлением или сразу после обновления необходимо переименовать существующие конфликтующие типы, определяемые пользователем.  
  
-   Geography  
  
-   Geometry  
  
-   Datetime2  
  
-   HierarchyID  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a>Целевая таблица для предложения OUTPUT INTO не может содержать определяемых триггеров.  
 Выходные данные в целевую таблицу, если в таблице определены какие-либо триггеры не поддерживается.  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a>Ошибки времени компиляции для определяемых пользователем функций в случаях, если целевой объект предложения OUTPUT INTO — таблица  
 Нельзя использовать определяемую пользователем функцию, чтобы выполнить действия, изменяющие состояние базы данных. Например, такая функция не может выполнять инструкции DDL (CREATE/ALTER/DROP) и DML (INSERT/UPDATE/DELETE) ни на каких объектах, кроме табличных переменных.  
  
## <a name="merge-is-a-reserved-keyword"></a>MERGE является зарезервированным ключевым словом.  
 MERGE теперь является полностью зарезервированным ключевым словом. Поэтому в приложениях не должно быть объектов (таблиц, столбцов и пр.) с именем MERGE.  
  
## <a name="rename-cdc-schema"></a>Переименование схемы CDC  
 Существует имя схемы CDC. Это имя схемы нельзя использовать, если **Change Data Capture** включен для базы данных.  
  
 Необходимо удалить схему CDC, прежде чем включать **Change Data Capture** для базы данных. Это можно сделать до обновления или после. Удаление схемы производится следующим образом.  
  
1.  Передайте объекты из схемы CDC в новую схему с помощью инструкции ALTER SCHEMA.  
  
2.  Проверьте разрешения на доступ к объектам в новой схеме.  
  
3.  Внесите необходимые изменения в приложение.  
  
4.  Удалите схему CDC с помощью инструкции DROP SCHEMA.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядра СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  

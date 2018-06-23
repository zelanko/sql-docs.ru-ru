---
title: Другие проблемы обновления Database Engine | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b1c74bf4ffd8cf0eba5cb853cccda80cc0b5d662
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087291"
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
 Вывод в целевую таблицу с помощью предложения OUTPUT INTO не поддерживается, если в таблице определены какие-либо триггеры.  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a>Ошибки времени компиляции для определяемых пользователем функций в случаях, если целевой объект предложения OUTPUT INTO — таблица  
 Нельзя использовать определяемую пользователем функцию, чтобы выполнить действия, изменяющие состояние базы данных. Например, такая функция не может выполнять инструкции DDL (CREATE/ALTER/DROP) и DML (INSERT/UPDATE/DELETE) ни на каких объектах, кроме табличных переменных.  
  
## <a name="merge-is-a-reserved-keyword"></a>MERGE является зарезервированным ключевым словом.  
 MERGE теперь является полностью зарезервированным ключевым словом. Поэтому в приложениях не должно быть объектов (таблиц, столбцов и пр.) с именем MERGE.  
  
## <a name="rename-cdc-schema"></a>Переименование схемы CDC  
 Существует имя схемы CDC. Это имя схемы нельзя использовать, если **измененных данных** включен для базы данных.  
  
 Необходимо удалить схему CDC, прежде чем включать **измененных данных** для базы данных. Это можно сделать до обновления или после. Удаление схемы производится следующим образом.  
  
1.  Передайте объекты из схемы CDC в новую схему с помощью инструкции ALTER SCHEMA.  
  
2.  Проверьте разрешения на доступ к объектам в новой схеме.  
  
3.  Внесите необходимые изменения в приложение.  
  
4.  Удалите схему CDC с помощью инструкции DROP SCHEMA.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
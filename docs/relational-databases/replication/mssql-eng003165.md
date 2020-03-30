---
title: MSSQL_ENG003165 | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: ac57d8427196b432f133f83f2e26be1ede88543f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287829"
---
# <a name="mssql_eng003165"></a>MSSQL_ENG003165
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3165|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|База данных '%ls' восстановлена, однако во время восстановления/удаления репликации произошла ошибка. База данных находится в режиме «вне сети». См. раздел MSSQL_ENG003165 в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка возникает, если возникает проблема восстановления резервной копии реплицированной базы данных:  
  
-   Если резервная копия восстанавливается в ту же базу данных на том же сервере, где создавалась эта резервная копия, ошибка указывает на то, что не удалось должным образом восстановить настройки репликации.  
  
-   Если резервная копия восстанавливается в другую базу данных или на другой сервер, ошибка указывает на то, что не удалось должным образом удалить настройки репликации (если база данных или сервер иные, настройки репликации удаляются по умолчанию).  
  
 Возможно, ошибка возникла в результате несовпадения состояний восстановленной базы данных и одной или нескольких системных баз данных, содержащих метаданные репликации: **msdb**, **master**или базы данных распространителя.  
  
## <a name="user-action"></a>Действие пользователя  
 Для разрешения этой проблемы:  
  
1.  Выполните команду ALTER DATABASE для перевода базы данных в режим "в сети", например, `ALTER DATABASE AdventureWorks SET ONLINE`. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md). Если требуется сохранить настройки репликации, перейдите к шагу 2. Если нет, перейдите к шагу 3.  
  
2.  Выполните процедуру [sp_restoredbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql.md). Если эта хранимая процедура выполнена успешно, восстановление завершено. Если она не будет выполнена успешно, перейдите к шагу 3.  
  
3.  Выполните процедуру [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md), чтобы удалить все настройки репликации.  
  
     При необходимости произведите повторную настройку репликации. Если скрипты топологии репликации были составлены в соответствии с рекомендациями, для повторной настройки топологии воспользуйтесь скриптами.  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Создание резервной копии и восстановление из копий реплицируемых баз данных](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

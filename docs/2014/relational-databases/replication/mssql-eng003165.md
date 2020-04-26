---
title: MSSQL_ENG003165 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4c2c6e01fd3e0b862511f71d90baf31d28948ef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62666710"
---
# <a name="mssql_eng003165"></a>MSSQL_ENG003165
    
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
  
1.  Выполните команду ALTER DATABASE для перевода базы данных в режим "в сети", например, `ALTER DATABASE AdventureWorks SET ONLINE`. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql). Если требуется сохранить настройки репликации, перейдите к шагу 2. Если нет, перейдите к шагу 3.  
  
2.  Выполните процедуру [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql). Если эта хранимая процедура выполнена успешно, восстановление завершено. Если она не будет выполнена успешно, перейдите к шагу 3.  
  
3.  Выполните процедуру [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql), чтобы удалить все настройки репликации.  
  
     При необходимости произведите повторную настройку репликации. Если скрипты топологии репликации были составлены в соответствии с рекомендациями, для повторной настройки топологии воспользуйтесь скриптами.  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление баз данных SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Создание резервной копии и восстановление из копий реплицируемых баз данных](administration/back-up-and-restore-replicated-databases.md)   
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  

---
title: sp_wait_for_database_copy_sync
titleSuffix: Azure SQL Database
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-dt-2019
ms.openlocfilehash: eb274d4f022a182ac056c190a8626fa48e36511d
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844397"
---
# <a name="active-geo-replication---sp_wait_for_database_copy_sync"></a>Активная Георепликация — sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Использование этой процедуры ограничено связью [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] между источником и получателем. Вызов **sp_wait_for_database_copy_sync** заставляет приложение ожидать, пока все зафиксированные транзакции не будут реплицированы и подтверждены активной базой данных-получателем. Запустите **sp_wait_for_database_copy_sync** только в базе данных источника.  
  
||  
|-|  
|**Применимо к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [@target_server =] "server_name"  
 Имя сервера базы данных SQL, на котором размещена активная база данных-получатель. Аргумент server_name имеет тип sysname и не имеет значения по умолчанию.  
  
 [@target_database =] "database_name"  
 Имя активной базы данных-получателя. Аргумент database_name имеет тип sysname и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Возвращает 0 при успешном завершений и номера ошибки в случае сбоя.  
  
 Наиболее вероятные условия возникновения ошибок:  
  
-   Отсутствует имя сервера или базы данных.  
  
-   Невозможно найти ссылку на заданное имя сервера или базы данных.  
  
-   Потеряно подключение к Interlink. **sp_wait_for_database_copy_sync** будет возвращено после истечения времени ожидания подключения.  
  
## <a name="permissions"></a>Разрешения  
 Эту системную хранимую процедуру может вызывать любой пользователь в базе данных-источнике. Имя входа должно быть пользователем и в базе данных-источнике, и в активной базе данных-получателе.  
  
## <a name="remarks"></a>Замечания  
 Все транзакции, зафиксированные до вызова **sp_wait_for_database_copy_sync** , отправляются в активную базу данных-получатель.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вызывается **sp_wait_for_database_copy_sync** , чтобы убедиться, что все транзакции фиксируются в базе данных-источнике Db0, а затем отправляются в свою активную базу данных-получатель на целевом сервере ubfyu5ssyt.  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>См. также раздел  
 [sys. dm_continuous_copy_status &#40;базы&#41; данных SQL Azure](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [Динамические административные представления и функции &#40;Георепликации база данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
  
  

---
title: "sp_kill_filestream_non_transacted_handles (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs: TSQL
helpviewer_keywords: sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d06550f0a9cd322e26acfa8f29890833c15f947
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="filestream-and-filetable---spkillfilestreamnontransactedhandles"></a>FileStream и FileTable - sp_kill_filestream_non_transacted_handles
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает нетранзакционные дескрипторы файлов для данных FileTable.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] ‘table_name’, [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_таблицы*  
 Имя таблицы, в которой следует закрыть нетранзакционные дескрипторы.  
  
 Можно передать *table_name* без *handle_id* чтобы закрыть все открытые нетранзакционные дескрипторы для FileTable.  
  
 Можно передать значение NULL для значения *table_name* закрыть все открытые нетранзакционные дескрипторы для всех таблиц Filetable в текущей базе данных. Значением по умолчанию является NULL.  
  
 *handle_id*  
 Дополнительный код отдельного дескриптора, который будет закрыт. Вы можете получить *handle_id* из [sys.dm_filestream_non_transacted_handles &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) динамическое административное представление. Каждый идентификатор уникален в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При указании *handle_id*, то также необходимо предоставить значение для *table_name*.  
  
 Можно передать значение NULL для значения *handle_id* чтобы закрыть все открытые нетранзакционные дескрипторы для FileTable, заданные *table_name*. Значением по умолчанию является NULL.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 *Handle_id* за счет **sp_kill_filestream_non_transacted_handles** не связан с session_id или единицей работы, которая используется в других **kill** команд.  
  
 Дополнительные сведения см. в статье [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Метаданные  
 Сведения об открытых нетранзакционных дескрипторов файлов, запросите динамическое административное представление [sys.dm_filestream_non_transacted_handles &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо иметь **VIEW DATABASE STATE** разрешение на получение дескрипторов файлов из **sys.dm_FILESTREAM_non_transacted_handles** динамического административного представления и для запуска **sp_kill_filestream_non_ transacted_handles**.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется вызов **sp_kill_filestream_non_transacted_handles** для закрытия дескрипторов нетранзакционных файлов для данных FileTable.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’, @handle_id = 0xFFFAAADD  
```  
  
 В следующем примере показано, как использовать сценарий для получения *handle_id* и закройте его.  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  

---
title: sp_kill_filestream_non_transacted_handles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7189499084c40d297f30514ba2f9bf5c01ada510
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52397647"
---
# <a name="spkillfilestreamnontransactedhandles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает нетранзакционные дескрипторы файлов для данных FileTable.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name*  
 Имя таблицы, в которой следует закрыть нетранзакционные дескрипторы.  
  
 Вы можете передать *table_name* без *handle_id* чтобы закрыть все открытые нетранзакционные дескрипторы для FileTable.  
  
 Можно передать NULL для значения *table_name* закрыть все открытые нетранзакционные дескрипторы для всех таблиц Filetable в текущей базе данных. Значением по умолчанию является NULL.  
  
 *handle_id*  
 Дополнительный код отдельного дескриптора, который будет закрыт. Вы можете получить *handle_id* из [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) динамическое административное представление. Каждый идентификатор уникален в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если указать *handle_id*, то необходимо также указать значение для *table_name*.  
  
 Можно передать NULL для значения *handle_id* закрыть все открытые нетранзакционные дескрипторы для таблицы FileTable, заданной *table_name*. Значением по умолчанию является NULL.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 *Handle_id* с требованиями **sp_kill_filestream_non_transacted_handles** не связана с идентификатором session_id или единицей работы, который используется в других **kill** команды.  
  
 Дополнительные сведения см. в статье [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Метаданные  
 Сведения об открытых нетранзакционный дескрипторов файлов, выполните запрос к динамическому административному представлению [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо иметь **VIEW DATABASE STATE** разрешение на получение дескрипторов файлов из **sys.dm_FILESTREAM_non_transacted_handles** динамического административного представления и для запуска **sp_kill_filestream_non_ transacted_handles**.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры показывают, как вызывать **sp_kill_filestream_non_transacted_handles** закрытие дескрипторов нетранзакционный файлов для данных FileTable.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
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
  
## <a name="see-also"></a>См. также  
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
 [FileStream и FileTable динамические административные представления (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[FileStream и представления каталога FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  

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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fdceccb1d11ce8818e9f26e46adf6b698e493cd4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898158"
---
# <a name="sp_kill_filestream_non_transacted_handles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Закрывает нетранзакционные дескрипторы файлов для данных FileTable.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name*  
 Имя таблицы, в которой следует закрыть нетранзакционные дескрипторы.  
  
 Можно передать *table_name* без *handle_id* , чтобы закрыть все открытые нетранзакционные дескрипторы для таблицы FileTable.  
  
 Можно передать значение NULL для значения *table_name* , чтобы закрыть все открытые нетранзакционные дескрипторы для всех таблиц FileTable в текущей базе данных. Значением по умолчанию является NULL.  
  
 *handle_id*  
 Дополнительный код отдельного дескриптора, который будет закрыт. *Handle_id* можно получить из динамического административного представления [sys. dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) . Каждый идентификатор уникален в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если указано *handle_id*, необходимо также указать значение для *table_name*.  
  
 Можно передать NULL в качестве значения *handle_id* , чтобы закрыть все открытые нетранзакционные дескрипторы для таблицы FileTable, указанной в *table_name*. Значением по умолчанию является NULL.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 *Handle_id* , необходимые **sp_kill_filestream_non_transacted_handles** , не связаны с session_id или единицей работы, используемыми в других командах **Kill** .  
  
 Дополнительные сведения см. в статье [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Метаданные  
 Для получения сведений об открытых нетранзакционных дескрипторах файлов запросите динамическое административное представление [sys. dm_filestream_non_transacted_handles &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Чтобы получить дескрипторы файлов из динамического административного представления **sys. dm_FILESTREAM_non_transacted_handles** и запуска **sp_kill_filestream_non_transacted_handles**, необходимо иметь разрешение **Просмотр состояния базы данных** .  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано, как вызвать **sp_kill_filestream_non_transacted_handles** , чтобы закрыть нетранзакционные дескрипторы файлов для данных FileTable.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
```  
  
 В следующем примере показано, как использовать скрипт для получения *handle_id* и его закрытия.  
  
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
 [Динамические административные представления FILESTREAM и FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[Представления каталога FILESTREAM и FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  

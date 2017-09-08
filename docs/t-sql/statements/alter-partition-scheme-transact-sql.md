---
title: "ALTER PARTITION SCHEME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION SCHEME
- ALTER_PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PARTITION SCHEME statement
- partition schemes [SQL Server], modifying
- modifying partition schemes
- adding filegroups
- NEXT USED filegroups
ms.assetid: f01d6880-9800-4cfb-8d11-d4be21efc8ca
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 545fe3da48f0d0c98d72b32e5a82d9fd55579d00
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-partition-scheme-transact-sql"></a>ALTER PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет файловую группу в схему секционирования или изменяет обозначение файловой группы NEXT USED для данной схемы секционирования.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER PARTITION SCHEME partition_scheme_name   
NEXT USED [ filegroup_name ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *partition_scheme_name*  
 Имя изменяемой схемы секционирования.  
  
 *filegroup_name*  
 Указывает файловую группу, которую требуется пометить для схемы секционирования как NEXT USED. Это означает, что файловая группа примет новое секционирование, создается с помощью [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md) инструкции.  
  
 В схеме секционирования только одна файловая группа может быть отмечена как NEXT USED. Можно указать пустую файловую группу. Если *имя_файловой_группы* указан и в настоящее время имеется файловая группа не отмечена как NEXT USED, *filegroup_name* отмечена как NEXT USED. Если *имя_файловой_группы* указано и файловая группа с пометкой NEXT USED уже существует, передает свойство NEXT USED с существующие файловую группу для *filegroup_name*.  
  
 Если *имя_файловой_группы* не указан и файловая группа с пометкой NEXT USED уже существует, эту файловую группу теряет состояние NEXT USED, чтобы не NEXT USED файловых групп в *partition_scheme_name*.  
  
 Если *filegroup_name* не указан, а не отмечена как NEXT USED, инструкция ALTER PARTITION SCHEME возвращает предупреждение.  
  
## <a name="remarks"></a>Замечания  
 Все файловые группы, на которые действует инструкция ALTER PARTITION SCHEME, должны быть в режиме «в сети».  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции ALTER PARTITION SCHEME необходимы следующие разрешения.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin** .  
  
-   Разрешение CONTROL или ALTER на базу данных, в которой была создана схема секционирования.  
  
-   Разрешения CONTROL SERVER или ALTER ANY DATABASE на сервер базы данных, в которой была создана схема секционирования.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что в базе данных существуют схема секционирования `MyRangePS1` и файловая группа `test5fg`.  
  
```  
ALTER PARTITION SCHEME MyRangePS1  
NEXT USED test5fg;  
```  
  
 Файловая группа `test5fg` получает любые дополнительные секции из секционированной таблицы или индекс как результат выполнения инструкции ALTER PARTITION FUNCTION.  
  
## <a name="see-also"></a>См. также:  
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_schemes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

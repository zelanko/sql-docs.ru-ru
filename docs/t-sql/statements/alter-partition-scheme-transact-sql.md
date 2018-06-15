---
title: ALTER PARTITION SCHEME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 90e2f54978561204b0fa7993df1d7dc3aa45bbf9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33067041"
---
# <a name="alter-partition-scheme-transact-sql"></a>ALTER PARTITION SCHEME (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Добавляет файловую группу в схему секционирования или изменяет обозначение файловой группы NEXT USED для данной схемы секционирования. 

>[!NOTE]
>В базе данных SQL Azure поддерживаются только первичные файловые группы.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER PARTITION SCHEME partition_scheme_name   
NEXT USED [ filegroup_name ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *partition_scheme_name*  
 Имя изменяемой схемы секционирования.  
  
 *filegroup_name*  
 Указывает файловую группу, которую требуется пометить для схемы секционирования как NEXT USED. Это означает, что файловая группа примет новое секционирование, созданное с помощью инструкции [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md).  
  
 В схеме секционирования только одна файловая группа может быть отмечена как NEXT USED. Можно указать пустую файловую группу. Если указан аргумент *filegroup_name* и ни одна файловая группа не является в данный момент NEXT USED, то группа *filegroup_name* помечается как NEXT USED. Если указан аргумент *filegroup_name* и файловая группа с пометкой NEXT USED уже существует, то свойство NEXT USED переносится от текущей файловой группы к группе *filegroup_name*.  
  
 Если аргумент *filegroup_name* не указан и файловая группа с пометкой NEXT USED уже существует, эта файловая группа теряет состояние NEXT USED, чтобы в схеме секционирования *partition_scheme_name* не осталось файловой группы NEXT USED.  
  
 Если аргумент *filegroup_name* не указан и ни одна файловая группа не отмечена как NEXT USED, инструкция ALTER PARTITION SCHEME возвращает предупреждение.  
  
## <a name="remarks"></a>Примечания  
 Все файловые группы, на которые действует инструкция ALTER PARTITION SCHEME, должны быть в режиме "в сети".  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкции ALTER PARTITION SCHEME необходимы следующие разрешения.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin**.  
  
-   Разрешение CONTROL или ALTER на базу данных, в которой была создана схема секционирования.  
  
-   Разрешения CONTROL SERVER или ALTER ANY DATABASE на сервер базы данных, в которой была создана схема секционирования.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что в базе данных существуют схема секционирования `MyRangePS1` и файловая группа `test5fg`.  
  
```  
ALTER PARTITION SCHEME MyRangePS1  
NEXT USED test5fg;  
```  
  
 Файловая группа `test5fg` получает любые дополнительные секции из секционированной таблицы или индекс как результат выполнения инструкции ALTER PARTITION FUNCTION.  
  
## <a name="see-also"></a>См. также  
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_schemes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [sys.data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

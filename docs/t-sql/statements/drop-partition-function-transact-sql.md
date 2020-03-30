---
title: DROP PARTITION FUNCTION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP PARTITION FUNCTION
- DROP_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting partition functions
- DROP PARTITION FUNCTION statement
- partition functions [SQL Server], removing
- dropping partition functions
- removing partition functions
ms.assetid: a4bb055a-a538-4db9-a6fb-550d1eabfa18
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ad8f9e49ea1dd22184384b337d036991d9dc7f9d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68044114"
---
# <a name="drop-partition-function-transact-sql"></a>DROP PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет функцию секционирования из текущей базы данных. Функции секционирования создаются с помощью инструкции CREATE PARTITION FUNCTION, а изменяются с помощью инструкции ALTER PARTITION FUNCTION.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP PARTITION FUNCTION partition_function_name [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *partition_function_name*  
 Имя функции секционирования, которую необходимо удалить.  
  
## <a name="remarks"></a>Remarks  
 Функцию секционирования можно удалить лишь в том случае, когда ни одна из схем секционирования на момент удаления не использует эту функцию. Если схемы секционирования используют функцию секционирования, инструкция DROP PARTITION FUNCTION возвратит ошибку.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкции DROP PARTITION FUNCTION требуется одно из следующих разрешений.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin** .  
  
-   Разрешение CONTROL или ALTER в базе данных, в которой была создана функция секционирования.  
  
-   Разрешение CONTROL SERVER или ALTER ANY DATABASE на сервере базы данных, в которой была создана функция секционирования.  
  
## <a name="examples"></a>Примеры  
 Следующий пример предполагает, что функция секционирования `myRangePF` создана в текущей базе данных.  
  
```  
DROP PARTITION FUNCTION myRangePF;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_functions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

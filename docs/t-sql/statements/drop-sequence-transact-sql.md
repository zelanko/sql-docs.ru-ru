---
title: DROP SEQUENCE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SEQUENCE
- DROP_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SEQUENCE statement
- sequence number object, dropping
ms.assetid: c25772d3-61af-4aa7-b58b-a6f67a793e3d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab35c07f176e3ae25303eb7693b8c2292b793559
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86483642"
---
# <a name="drop-sequence-transact-sql"></a>DROP SEQUENCE (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Удаляет объект последовательности из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DROP SEQUENCE [ IF EXISTS ] { database_name.schema_name.sequence_name | schema_name.sequence_name | sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление последовательности только в том случае, если она уже существует.  
  
 *database_name*  
 Имя базы данных, в которой создан объект последовательности.  
  
 *schema_name*  
 Имя схемы, которой принадлежит объект последовательности.  
  
 *sequence_name*  
 Имя последовательности, которую нужно удалить. Тип **sysname**.  
  
## <a name="remarks"></a>Remarks  
 После создания числа объект последовательности не имеет постоянной связи с созданным им числом, так что объект последовательности можно удалить, несмотря на то, что созданное число еще используется.  
  
 Объект последовательности можно удалить, даже если на него ссылается хранимая процедура или триггер, поскольку он не привязан к схеме. Объект последовательности нельзя удалить, если на него есть ссылка как на значение по умолчанию в таблице. В сообщении об ошибке будет указан объект, который ссылается на последовательность.  
  
 Чтобы получить список всех объектов последовательности в базе данных, выполните следующую инструкцию.  
  
```  
SELECT sch.name + '.' + seq.name AS [Sequence schema and name]   
    FROM sys.sequences AS seq  
    JOIN sys.schemas AS sch  
        ON seq.schema_id = sch.schema_id ;  
GO  
```  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER или CONTROL для схемы.  
  
### <a name="audit"></a>Аудит  
 Для аудита функции **DROP SEQUENCE** отслеживайте **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере объект последовательности с именем `CountBy1` удаляется из текущей базы данных.  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SEQUENCE (Transact-SQL)](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [CREATE SEQUENCE (Transact-SQL)](../../t-sql/statements/create-sequence-transact-sql.md)   
 [NEXT VALUE FOR (Transact-SQL)](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

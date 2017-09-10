---
title: "DROP ПОСЛЕДОВАТЕЛЬНОСТИ (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d7247c5e809c8e26fbd17dc01e8c2f624a170ff
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-sequence-transact-sql"></a>DROP SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Удаляет объект последовательности из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP SEQUENCE [ IF EXISTS ] { [ database_name . [ schema_name ] . | schema_name. ]    sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет последовательность только в том случае, если он уже существует.  
  
 *database_name*  
 Имя базы данных, в которой создан объект последовательности.  
  
 *schema_name*  
 Имя схемы, которой принадлежит объект последовательности.  
  
 *sequence_name*  
 Имя последовательности, которую нужно удалить. Тип — **sysname**.  
  
## <a name="remarks"></a>Замечания  
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
  
### <a name="permissions"></a>Permissions  
 Требуется разрешение ALTER или CONTROL для схемы.  
  
### <a name="audit"></a>Аудит  
 Для аудита **DROP SEQUENCE**, монитор **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере объект последовательности с именем `CountBy1` удаляется из текущей базы данных.  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER ПОСЛЕДОВАТЕЛЬНОСТИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Создание ПОСЛЕДОВАТЕЛЬНОСТИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [СЛЕДУЮЩЕЕ значение для &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  


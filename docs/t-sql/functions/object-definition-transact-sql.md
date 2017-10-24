---
title: "OBJECT_DEFINITION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_DEFINITION_TSQL
- OBJECT_DEFINITION
dev_langs:
- TSQL
helpviewer_keywords:
- viewing source text
- source text [SQL Server]
- displaying source text
- OBJECT_DEFINITION function
ms.assetid: 2ac837c7-eca9-4d29-b06e-72e30450c68d
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fcb2ac9e5dd80c804996d08b084b4b0068c4b618
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="objectdefinition-transact-sql"></a>OBJECT_DEFINITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает исходный текст [!INCLUDE[tsql](../../includes/tsql-md.md)] определения указанного объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OBJECT_DEFINITION ( object_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта, который будет использован. *object_id* — **int**и представляет объект в контексте текущей базы данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(max)**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как OBJECT_DEFINITION, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Предполагается, что *object_id* находится в контексте текущей базы данных. Параметры сортировки определения объекта всегда совпадают с параметрами сортировки контекста вызывающей базы данных.  
  
 OBJECT_DEFINITION применяется к объектам следующих типов:  
  
-   C = проверочное ограничение;  
  
-   D = значение по умолчанию (ограничение или изолированное);  
  
-   P = хранимая процедура SQL  
  
-   FN = скалярная функция SQL  
  
-   R = правило  
  
-   RF = процедура фильтра репликации;  
  
-   TR = триггер SQL (триггер DML, существующий в пределах схемы, или триггер DDL в области базы данных или сервера);  
  
-   IF = встроенная функция SQL с табличным значением  
  
-   TF = возвращающая табличное значение функция SQL;  
  
-   V = представление  
  
## <a name="permissions"></a>Permissions  
 Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или участникам, которым предоставлены следующие разрешения: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION. Эти разрешения неявно предоставляются членам предопределенных ролей базы данных **db_owner**, **db_ddladmin**и **db_securityadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-source-text-of-a-user-defined-object"></a>A. Возвращение исходного текста пользовательского объекта  
 В следующем примере возвращается определение пользовательского триггера `uAddress` в схеме `Person`. Встроенная функция `OBJECT_ID` используется, чтобы передать идентификатор объекта триггера в инструкцию `OBJECT_DEFINITION`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.uAddress')) AS [Trigger Definition];   
GO  
```  
  
### <a name="b-returning-the-source-text-of-a-system-object"></a>Б. Возвращение исходного текста системного объекта  
 В следующем примере возвращается определение системной хранимой процедуры `sys.sp_columns`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'sys.sp_columns')) AS [Object Definition];  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [Object_name &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
  


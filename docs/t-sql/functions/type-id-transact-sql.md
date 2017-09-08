---
title: "Type_id (Transact-SQL) | Документы Microsoft"
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
- TYPE_ID
- TYPE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], types
- TYPE_ID function
- type IDs [SQL Server]
- data types [SQL Server], IDs
ms.assetid: 647d17ef-b878-4922-b446-56642322ebad
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a90c27d9d5d599a607306641958c1dcbc94aec79
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="typeid-transact-sql"></a>TYPE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает идентификатор для указанного имени типа данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TYPE_ID ( [ schema_name ] type_name )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Функция TYPE_NAME*  
 Имя типа данных. *Функция TYPE_NAME* относится к типу **nvarchar**. *Функция TYPE_NAME* может быть системный или определяемый пользователем тип.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как TYPE_ID могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Замечания  
 Функция TYPE_ID возвращает NULL, если имя типа неверно или если вызывающий не имеет необходимых разрешений на использование этого типа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-looking-up-the-type-id-values-for-single--and-two-part-type-names"></a>A. Поиск значений функции TYPE ID для имен типов, состоящих из одной и двух частей  
 В следующем примере возвращается идентификатор для имен типов, состоящих из одной и двух частей.  
  
```  
USE tempdb;  
GO  
CREATE TYPE NewType FROM int;  
GO  
CREATE SCHEMA NewSchema;  
GO  
CREATE TYPE NewSchema.NewType FROM int;  
GO  
SELECT TYPE_ID('NewType') AS [1 Part Data Type ID],  
       TYPE_ID('NewSchema.NewType') AS [2 Part Data Type ID];  
GO  
```  
  
### <a name="b-looking-up-the-type-id-of-a-system-data-type"></a>Б. Поиск значения функции TYPE ID для системного типа данных  
 В следующем примере возвращается значение `TYPE ID` для системного типа данных `datetime`.  
  
```  
SELECT TYPE_NAME(TYPE_ID('datetime')) AS [TYPE_NAME]  
    ,TYPE_ID('datetime') AS [TYPE_ID];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-looking-up-the-type-id-of-a-system-data-type"></a>C: поиске функции TYPE ID для системного типа данных  
 В следующем примере возвращается значение `TYPE ID` для системного типа данных `datetime`.  
  
```  
SELECT TYPE_NAME(TYPE_ID('datetime')) AS typeName,   
    TYPE_ID('datetime') AS typeID FROM table1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция TYPE_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/type-name-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
  
  



---
title: "Тип удаления (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4187c6bff08e5502f5edc6acd8d82334684a68d4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет псевдоним типа данных или пользовательский тип данных среды CLR из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно Удаляет тип только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, к которой относится тип псевдонима или пользовательский тип.  
  
 *Функция TYPE_NAME*  
 Имя псевдонима типа данных или пользовательского типа, который необходимо удалить.  
  
## <a name="remarks"></a>Замечания  
 Инструкция DROP TYPE не будет выполняться, если что-либо из перечисленного ниже справедливо.  
  
-   В базе данных есть таблицы, содержащие столбцы с псевдонимом типа данных или определяемым пользователем типом данных. Сведения о псевдоним или столбцов определяемого пользователем типа можно получить с помощью запроса [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) или [sys.column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md) представления каталога.  
  
-   На псевдоним типа данных или пользовательский тип данных ссылаются определения вычисляемых столбцов, ограничений CHECK, привязанных к схеме представлений и функций. Сведения о данных ссылках можно получить с помощью запроса [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) представления каталога.  
  
-   В базе данных созданы функции, хранимые процедуры или триггеры, и эти процедуры используют переменные и параметры с псевдонимом типа данных или пользовательским типом данных. Сведения о псевдоним или параметры определяемого пользователем типа можно получить с помощью запроса [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) или [sys.parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md) представления каталога.  
  
## <a name="permissions"></a>Permissions  
 Требует либо разрешения CONTROL на *type_name* или разрешение ALTER для *schema_name*.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется тип данных с названием `ssn`, уже созданный в текущей базе данных.  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


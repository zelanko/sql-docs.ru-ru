---
title: COL_LENGTH (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COL_LENGTH
- COL_LENGTH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- lengths [SQL Server], columns
- COL_LENGTH function
- column properties [SQL Server]
- column length [SQL Server]
ms.assetid: cf891206-c49f-40eb-858e-eefd2b638a33
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9e7ff86386eac4bdc30680cc763a2b11e522076c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="collength-transact-sql"></a>COL_LENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает длину столбца в байтах.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COL_LENGTH ( 'table' , 'column' )   
```  
  
## <a name="arguments"></a>Аргументы  
**'** *table* **'**  
Имя таблицы, для которой необходимо получить сведения о длине столбца. *table* — это выражение типа **nvarchar**.
  
**'** *column* **'**  
Имя столбца, длину которого требуется определить. *column* — это выражение типа **nvarchar**.
  
## <a name="return-type"></a>Возвращаемый тип
**smallint**
  
## <a name="exceptions"></a>Исключения  
Возвращает значение NULL в случае ошибки или если участник не имеет правильных разрешений для просмотра объекта.
  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как COL_LENGTH, могут вернуть значение NULL в случае, если у пользователя нет правильных разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Remarks  
Для столбцов **varchar**, объявленных с описателем **max** (**varchar(max)**), функция COL_LENGTH возвращает значение –1.
  
## <a name="examples"></a>Примеры  
В этом примере демонстрируются возвращаемые значения для столбца типа `varchar(40)` и для столбца типа `nvarchar(40)`.
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE t1(c1 varchar(40), c2 nvarchar(40) );  
GO  
SELECT COL_LENGTH('t1','c1')AS 'VarChar',  
      COL_LENGTH('t1','c2')AS 'NVarChar';  
GO  
DROP TABLE t1;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
VarChar     NVarChar  
40          80  
```  
  
## <a name="see-also"></a>См. также раздел
[Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
[Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COL_NAME (Transact-SQL)](../../t-sql/functions/col-name-transact-sql.md)  
[COLUMNPROPERTY (Transact-SQL)](../../t-sql/functions/columnproperty-transact-sql.md)
  
  

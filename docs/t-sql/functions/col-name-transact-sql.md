---
title: COL_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7750eab9dd1e5ff24ee94f38979df03275091964
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944077"
---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает имя столбца таблицы на основе значений идентификационного номера таблицы и столбца для этого столбца таблицы.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>Аргументы  
*table_id*  
Идентификационный номер таблицы, содержащей этот столбец. Аргумент *table_id* имеет тип данных **int**.
  
*column_id*  
Идентификационный номер столбца. Аргумент *column_id* имеет тип данных **int**.
  
## <a name="return-types"></a>Типы возвращаемых данных
**sysname**
  
## <a name="exceptions"></a>Исключения  
Возвращает значение NULL в случае ошибки или если участник не имеет правильных разрешений для просмотра объекта.
  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые ему были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как `COL_NAME`, могут вернуть значение NULL в случае, если у пользователя нет правильных разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Remarks  
Аргументы *table_id* и *column_id* совместно образуют строку имени столбца.
  
Дополнительные сведения о получении идентификационных номеров таблиц и столбцов см. в статье [OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md).
  
## <a name="examples"></a>Примеры  
В этом примере возвращается имя первого столбца в образце таблицы `Employee`.
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>См. также раздел
[Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
[Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY (Transact-SQL)](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH (Transact-SQL)](../../t-sql/functions/col-length-transact-sql.md)
  
  


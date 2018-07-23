---
title: DROP SENSITIVITY CLASSIFICATION (Transact-SQL) | Документация Майкрософт
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- DROP SENSITIVITY CLASSIFICATION
- DROP_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SENSITIVITY CLASSIFICATION statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 7571742d0484065a90734ad9d9972e37076e20d3
ms.sourcegitcommit: 70882926439a63ab9d812809429c63040eb9a41b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36262872"
---
# <a name="drop-sensitivity-classification-transact-sql"></a>DROP SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Удаляет метаданные о классификации конфиденциальности из одного или нескольких столбцов базы данных.

## <a name="syntax"></a>Синтаксис

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    <object_name> [, ...n ]

<object_name> ::=
{
    [schema_name.]table_name.column_name
}
```  

## <a name="arguments"></a>Аргументы  

*object_name* ([schema_name.]table_name.column_name)

Имя столбца базы данных, для которого удаляются сведения. Сейчас поддерживается только классификация по столбцам.
    - *schema_name* (необязательно) — имя схемы, которая содержит классифицируемый столбец.
    - *table_name* — имя таблицы, которая содержит классифицируемый столбец.
    - *column_name* — имя столбца, для которого удаляется классификация.

## <a name="remarks"></a>Remarks  

- Несколько классификаций объектов можно удалить с помощью одной инструкции DROP SENSITIVITY CLASSIFICTION.

## <a name="permissions"></a>Разрешения  

Требуется разрешение ALTER ANY SENSITIVITY CLASSIFICATION. Разрешение ALTER ANY SENSITIVITY CLASSIFACTION содержится в разрешении ALTER для базы данных или CONTROL SERVER для сервера.


## <a name="examples"></a>Примеры  


### <a name="a-dropping-classification-from-a-single-column"></a>A. Удаление классификации из одного столбца

В следующем примере классификация удаляется из столбца `dbo.sales.price`.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price
```

### <a name="b-dropping-classification-from-multiple-columns"></a>Б. Удаление классификации из нескольких столбцов

В следующем примере классификация удаляется из столбцов `dbo.sales.price`, `dbo.sales.discount` и `SalesLT.Customer.Phone`.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price, dbo.sales.discount, SalesLT.Customer.Phone  
```

## <a name="see-also"></a>См. также:  

[ADD SENSITIVITY CLASSIFICTION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Начало работы с SQL Information Protection](http://aka.ms/sqlip)

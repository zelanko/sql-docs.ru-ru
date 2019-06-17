---
title: ADD SENSITIVITY CLASSIFICATION (Transact-SQL) | Документация Майкрософт
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- ADD SENSITIVITY CLASSIFICATION
- ADD_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SENSITIVITY CLASSIFICATION statement
- add labels
- adding labels
- adding labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9e4fee7a2504255b0763cf9cfad708fd341d336d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62712371"
---
# <a name="add-sensitivity-classification-transact-sql"></a>ADD SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Добавляет метаданные о классификации по уровням конфиденциальности в один или несколько столбцов базы данных. Эта классификация может включать метки конфиденциальности и тип данных.  

Классификация конфиденциальных данных в среде базы данных позволяет повысить видимость и уровень защиты данных. Дополнительные сведения см. в статье [Обнаружение и классификация данных в службе "База данных SQL Azure"](https://aka.ms/sqlip).

## <a name="syntax"></a>Синтаксис  

```sql
ADD SENSITIVITY CLASSIFICATION TO
    <object_name> [, ...n ]
    WITH ( <sensitivity_label_option> [, ...n ] )     

<object_name> ::=
{
    [schema_name.]table_name.column_name
}

<sensitivity_label_option> ::=  
{   
    LABEL = string |
    LABEL_ID = guidOrString |
    INFORMATION_TYPE = string |
    INFORMATION_TYPE_ID = guidOrString  
}
```  

## <a name="arguments"></a>Аргументы  

*object_name* ([schema_name.]table_name.column_name)

Это имя столбца базы данных, к которому применяется классификация. Сейчас поддерживается только классификация по столбцам.
    - *schema_name* (необязательно) — имя схемы, которая содержит классифицированный столбец.
    - *table_name* — имя таблицы, которая содержит классифицированный столбец.
    - *column_name* — имя классифицированного столбца.

*LABEL*

Понятная для пользователя метка конфиденциальности. Метки конфиденциальности описывают уровень конфиденциальности данных, хранящихся в определенном столбце базы данных.

*LABEL_ID*

Это идентификатор, связанный с меткой конфиденциальности. Он часто используется в централизованных платформах защиты информации для уникальной идентификации метки в системе.

*INFORMATION_TYPE*

Понятное для пользователя имя типа информации. Типы информации используются для описания типов данных, хранящихся в столбцах базы данных.

*INFORMATION_TYPE_ID*

Идентификатор, связанный с типом информации. Он часто используется в централизованных платформах защиты информации для уникальной идентификации типов информации в системе.


## <a name="remarks"></a>Remarks  

- К одному объекту можно добавить только одну классификацию. Если вы попытаетесь добавить классификацию к объекту, который уже имеет другую классификацию, прежняя классификация будет удалена.
- Вы можете классифицировать сразу несколько объектов с помощью одной инструкции `ADD SENSITIVITY CLASSIFICATION`.
- Системное представление [sys.sensitivity_classifications](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md) позволяет получать информацию о классификации конфиденциальности для базы данных.


## <a name="permissions"></a>Разрешения

Требуется разрешение ALTER ANY SENSITIVITY CLASSIFICATION. ALTER ANY SENSITIVITY CLASSIFICATION подразумевается в разрешении ALTER для базы данных или CONTROL SERVER для сервера.


## <a name="examples"></a>Примеры  

### <a name="a-classifying-two-columns"></a>A. Классификация двух столбцов

В следующем примере столбцам **dbo.sales.price** и **dbo.sales.discount** присваивается метка конфиденциальности **Highly Confidential** (Строго конфиденциально) и тип сведений **Financial** (Финансовые).

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.sales.price, dbo.sales.discount
    WITH ( LABEL='Highly Confidential', INFORMATION_TYPE='Financial' )
```  

### <a name="b-classifying-only-a-label"></a>Б. Классификация только для метки
В следующем примере столбцу **dbo.customer.comments** присваивается метка **Confidential** (Конфиденциально) и идентификатор метки **643f7acd-776a-438d-890c-79c3f2a520d6**. Для этого столбца тип информации не классифицируется.

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.customer.comments
    WITH ( LABEL='Confidential', LABEL_ID='643f7acd-776a-438d-890c-79c3f2a520d6' )
```  

## <a name="see-also"></a>См. также:  

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Разрешения (ядро СУБД)](https://docs.microsoft.com/sql/relational-databases/security/permissions-database-engine)

[Обнаружение и классификация данных в службе "База данных SQL Azure"](https://aka.ms/sqlip)

---
title: "COLUMNPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMNPROPERTY
- COLUMNPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- parameters [SQL Server], properties
- COLUMNPROPERTY function
ms.assetid: 2408c264-6eca-4120-bb71-df043c7c2792
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: c6c2af8d231f03c40ee87d3468977c3b66cbeeb4
ms.contentlocale: ru-ru
ms.lasthandoff: 10/05/2017

---
# <a name="columnproperty-transact-sql"></a>COLUMNPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает сведения о столбце или о параметре.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COLUMNPROPERTY ( id , column , property )   
```  
  
## <a name="arguments"></a>Аргументы  
*идентификатор*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) , содержащий идентификатор (ID) таблицы или процедуры.
  
*столбец*  
Выражение, которое содержит имя столбца или параметра.
  
*Свойство*  
Выражение, которое содержит сведения, которые необходимо вернуть для *идентификатор*, и может принимать одно из следующих значений.
  
|Значение|Description|Возвращенное значение|  
|---|---|---|
|**AllowsNull**|Разрешение использовать NULL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**ColumnId**|Значение идентификатора столбца, соответствующего **sys.columns.column_id**.|Идентификатор столбца<br /><br /> **Примечание:** могут появиться при запросе множества столбцов, пропуски в последовательности значений Идентификаторов столбца.|  
|**FullTextTypeColumn**|Тип СТОЛБЦА в таблице, которая содержит информацию о типе документа *столбца*.|Идентификатор полнотекстового TYPE COLUMN для столбцов, переданных вторым параметром этого свойства.|  
|**IsComputed**|Столбец является вычисляемым столбцом.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsCursorType**|Параметр процедуры имеет тип CURSOR.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsDeterministic**|Столбцы являются детерминированными (предсказуемыми). Это свойство применимо только к вычисляемым столбцам и столбцам представлений.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы. Невычисляемый столбец или не столбец представлений.|  
|**IsFulltextIndexed**|Столбцы отмечены для полнотекстовой индексации.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsIdentity**|Столбец использует свойство IDENTITY.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsIdNotForRepl**|Столбец проверяет настройку IDENTITY_INSERT.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsIndexable**|Столбцы не могут быть индексированы.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsOutParam**|Параметр процедуры является выходным параметром.|1 = TRUE<br /><br /> 0 = FALSE NULL = введенные значения недопустимы.|  
|**IsPrecise**|Точный столбец. Это свойство применимо только к детерминированным столбцам.|1 = TRUE<br /><br /> 0 = FALSE NULL = введенные значения недопустимы. Недетерминированный столбец|  
|**IsRowGuidCol**|Столбец имеет **uniqueidentifier** тип данных и определяется со свойством ROWGUIDCOL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsSystemVerified**|Свойства детерминированности и точности столбца могут быть проверены с помощью [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Это свойство применимо только к вычисляемым столбцам и столбцам представлений.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsXmlIndexable**|XML-столбец может быть использован в XML-индексе.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**Точность**|Длина для типа данных в столбце или для параметра.|Длина заданного типа данных столбца<br /><br /> -1 = **xml** или типы больших значений<br /><br /> NULL = Введенные значения недопустимы.|  
|**Масштаб**|Масштаб для типа данных в столбце или для параметра.|Масштаб<br /><br /> NULL = Введенные значения недопустимы.|  
|**StatisticalSemantics**|Столбец доступен для семантического индексирования.|1 = TRUE<br /><br /> 0 = FALSE|  
|**SystemDataAccess**|Столбец, полученный из функции, которая получает данные в системных каталогах или виртуальных системных таблицах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это свойство применимо только к вычисляемым столбцам и столбцам представлений.|1 = TRUE (обозначает доступ только для чтения)<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**UserDataAccess**|Столбец, полученный из функции, которая получает данные в пользовательских таблицах, включая таблицы видов и временные таблицы, хранится в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это свойство применимо только к вычисляемым столбцам и столбцам представлений.|1 = TRUE (обозначает доступ только для чтения)<br /><br /> 0 = FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**UsesAnsiTrim**|ANSI_PADDING был установлен как ON, если таблица была создана впервые. Это свойство применяется только к столбцам или параметрам типа **char** или **varchar**.|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsSparse**|Столбец является разреженным столбцом. Дополнительные сведения см. в статье [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**IsColumnSet**|Столбец представляет собой набор столбцов. Дополнительные сведения см. в статье [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).|1= TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Введенные значения недопустимы.|  
|**GeneratedAlwaysType**|Значение столбца, созданные системой. Соответствует **sys.columns.generated_always_type**|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = не созданный в всегда<br /><br /> 1 = создаваемые всегда как начало строки<br /><br /> 2 — всегда создаваемый как конец строки|  
|**IsHidden**|Значение столбца, созданные системой. Соответствует **sys.columns.is_hidden**|**Область применения**: начиная с [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = не скрытые<br /><br /> 1 = Hidden|  
  
## <a name="return-types"></a>Возвращаемые типы
 **int**  
  
## <a name="exceptions"></a>Исключения  
Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.
  
Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как COLUMNPROPERTY, могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Замечания  
Если проверяется детерминистическое свойство столбца, сначала нужно проверить, является ли столбец вычисляемым. **IsDeterministic** возвращает значение NULL для невычисляемых столбцов. Вычисляемые столбцы могут быть определены как индексированные столбцы.
  
## <a name="examples"></a>Примеры  
Следующий пример возвращает длину столбца `LastName`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT COLUMNPROPERTY( OBJECT_ID('Person.Person'),'LastName','PRECISION')AS 'Column Length';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Column Length
-------------
50
```  
  
## <a name="see-also"></a>См. также:
[Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)
  
  


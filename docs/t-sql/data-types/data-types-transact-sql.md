---
title: "Типы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system data types [SQL Server]
- data types [SQL Server]
- data types [SQL Server], about data types
ms.assetid: a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: a37fc487615827eb2a380c3fe608b9c29cfda3a8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/14/2017

---

# <a name="data-types-transact-sql"></a>Типы данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] у каждого столбца, локальной переменной, выражения и параметра есть определенный тип данных. Тип данных — атрибут, определяющий, какого рода данные могут храниться в объекте: целые числа, символы, данные денежного типа, метки времени и даты, двоичные строки и так далее.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет набор системных типов данных, определяющих все типы данных, которые можно использовать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно также определить собственные типы данных в [!INCLUDE[tsql](../../includes/tsql-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Псевдонимы типов данных основываются на системных типах. Дополнительные сведения о псевдонимах типов данных см. в разделе [CREATE TYPE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-type-transact-sql.md). Определяемые пользователем типы данных обладают свойствами, зависящими от методов и операторов класса, который создается для них на одном из языков программирования, которые поддерживаются [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].
  
При объединении одним оператором двух выражений с разными типами данных, параметрами сортировки, точностями, масштабами или длинами, результат определяется следующим образом.
-   Тип данных результата определяется применением правил очередности типов данных к входным выражениям. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
-   Параметры сортировки результата определяются правилами очередности параметров сортировки при тип данных результата относится **char**, **varchar**, **текст**, **nchar**, **nvarchar**, или **ntext**. Дополнительные сведения см. в разделе [очередность параметров сортировки &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).  
-   Точность, масштаб и длина результата зависят от точности, масштаба и длины входных выражений. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет синонимы типов данных для совместимости со стандартом ISO. Дополнительные сведения см. в разделе [синонимы типов данных &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
## <a name="data-type-categories"></a>Категории типов данных
Типы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] организованы в следующие категории:
  
|||  
|-|-|  
|Точные числа|Символьные строки в Юникоде|  
|Приблизительные числа|Двоичные данные|  
|Дата и время|Прочие типы данных|  
|Символьные строки||  
  
В зависимости от параметров хранения, некоторые типы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] относятся к следующим группам:
-   Типы данных больших значений: **varchar(max)**, и **nvarchar(max)**  
-   Типы данных больших объектов: **текст**, **ntext**, **изображения**, **varbinary(max)**, и **xml**  
  
    > [!NOTE]  
    >  sp_help возвращает -1 в качестве длины для большого объема и **xml** типов данных.  
  
### <a name="exact-numerics"></a>Точные числа
  
|||  
|-|-|  
|[bigint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[decimal](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|[smallmoney](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[money](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)||  
  
### <a name="approximate-numerics"></a>Приблизительные числа
  
|||  
|-|-|  
|[float](../../t-sql/data-types/float-and-real-transact-sql.md)|[real](../../t-sql/data-types/float-and-real-transact-sql.md)|  
  
### <a name="date-and-time"></a>Дата и время
  
|||  
|-|-|  
|[date](../../t-sql/data-types/date-transact-sql.md)|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|[time](../../t-sql/data-types/time-transact-sql.md)|  
  
### <a name="character-strings"></a>Символьные строки
  
|||  
|-|-|  
|[char;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|[varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|[text](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="unicode-character-strings"></a>Символьные строки в Юникоде
  
|||  
|-|-|  
|[nchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|[nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
|[ntext](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="binary-strings"></a>Двоичные данные
  
|||  
|-|-|  
|[binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|[image](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="other-data-types"></a>Прочие типы данных
  
|||  
|-|-|  
|[курсор](../../t-sql/data-types/cursor-transact-sql.md)|[timestamp](../../t-sql/data-types/rowversion-transact-sql.md)|  
|[hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md)|  
|[sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md)|[xml](../../t-sql/xml/xml-transact-sql.md)|  
|[Геометрических пространственных типов](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md) |[Географические Пространственные типы](../../t-sql/spatial-geography/spatial-types-geography.md)|  
|[table](../../t-sql/data-types/table-transact-sql.md) | |
  
## <a name="see-also"></a>См. также:
[CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[ОБЪЯВИТЕ @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [EXECUTE &#40; Transact-SQL &#41;](../../t-sql/language-elements/execute-transact-sql.md)  
[Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
[Функции &#40; Transact-SQL &#41;](../../t-sql/functions/functions.md)  
[КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[Хранимая процедура sp_droptype &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)  
[sp_help &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)  
[процедура sp_rename &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)
  
  


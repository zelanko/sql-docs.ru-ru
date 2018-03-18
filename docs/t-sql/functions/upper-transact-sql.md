---
title: "UPPER (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPPER_TSQL
- UPPER
dev_langs:
- TSQL
helpviewer_keywords:
- UPPER function
- characters [SQL Server], lowercase
- converting lowercase to uppercase
- uppercase characters [SQL Server]
- characters [SQL Server], uppercase
- lowercase characters
ms.assetid: 5ced55f7-ac89-4cf2-9465-f63f4dc480db
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7fc98d515cef0d4a1f11e44ada8ff45174b8c95e
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="upper-transact-sql"></a>UPPER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьное выражение, в котором символы нижнего регистра преобразованы в символы верхнего регистра.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
UPPER ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьного типа данных. Аргумент *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
 Аргумент *character_expression* должен иметь тип данных, который может быть неявно преобразован в тип **varchar**. В противном случае используйте [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *character_expression*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar** или **nvarchar**  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере функции `UPPER` и `RTRIM` используются для получения из таблицы `dbo.DimEmployee` фамилий всех людей, при этом все символы фамилии преобразуются в верхний регистр, соответствующая символьная строка обрезается и производится ее сцепление со строкой имени.  
  
```  
-- Uses AdventureWorks  
  
SELECT UPPER(RTRIM(LastName)) + ', ' + FirstName AS Name  
FROM dbo.DimEmployee  
ORDER BY LastName;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
Name
------------------------------
ABBAS, Syed
ABERCROMBIE, Kim
ABOLROUS, Hazem
 ```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
 [LOWER (Transact-SQL)](../../t-sql/functions/lower-transact-sql.md)  
  
  


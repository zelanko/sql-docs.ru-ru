---
description: SPACE (Transact-SQL)
title: SPACE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SPACE_TSQL
- SPACE
dev_langs:
- TSQL
helpviewer_keywords:
- strings [SQL Server], repeated spaces
- repeated spaces
- SPACE function
ms.assetid: b4fac3b8-2d47-4c11-a6a6-009e5a538f40
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f2d02a2ff302b88c8af676200997978e750cf49
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467854"
---
# <a name="space-transact-sql"></a>SPACE (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает строку пробелов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
SPACE ( integer_expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *integer_expression*  
 Положительное целое число, определяющее количество пробелов в строке. Если аргумент *integer_expression* отрицателен, то возвращается пустая строка.  
  
 Дополнительные сведения см. в статье [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **varchar**  
  
## <a name="remarks"></a>Remarks  
 Чтобы включить в строку пробелы в формате Юникод или возвратить более 8000 пробелов, используйте вместо функции SPACE функцию REPLICATE.  
  
## <a name="examples"></a>Примеры  
 Следующий пример исключает пробелы из фамилий людей, указанных в таблице `Person` базы данных `AdventureWorks2012`, и дополняет их фамилии запятой, двумя пробелами и именами.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM Person.Person  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример исключает пробелы из фамилий людей, указанных в таблице `DimCustomer` базы данных `AdventureWorksPDW2012`, и дополняет их фамилии запятой, двумя пробелами и именами.  
  
```  
-- Uses AdventureWorks  
  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM dbo.DimCustomer  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [REPLICATE (Transact-SQL)](../../t-sql/functions/replicate-transact-sql.md)   
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  



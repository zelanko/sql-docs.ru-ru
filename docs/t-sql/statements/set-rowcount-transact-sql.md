---
title: "SET ROWCOUNT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eda7f9faf2bb45b06cf1112dbe48cbdb281fdab3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Приводит к завершению обработки запроса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после возвращения указанного количества строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SET ROWCOUNT { number | @number_var }   
```  
  
## <a name="arguments"></a>Аргументы  
 *номер* | @*number_var*  
 Количество строк, выраженное целым числом, которое необходимо обработать, перед завершением запроса.  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Использование инструкции SET ROWCOUNT не будет оказывать влияния на инструкции DELETE, INSERT и UPDATE в последующей версии SQL Server. При программировании избегайте использования инструкции SET ROWCOUNT с инструкциями DELETE, INSERT и UPDATE и постарайтесь внести изменения в приложения, которые используют ее в настоящее время. Для аналогичного поведения используйте синтаксис TOP. Дополнительные сведения см. в разделе [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 Для выключения этого параметра и возвращения всех строк, укажите SET ROWCOUNT 0.  
  
 Установка параметра ROWCOUNT приводит к тому, что большинство инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] прекращают обработку, если на них влияет указанное число строк. Это включает триггеры. Параметр ROWCOUNT не влияет на динамические курсоры, но ограничивает набор строк набора ключей и нечувствительных курсоров. Пользоваться этим параметром следует осторожно.  
  
 Инструкция SET ROWCOUNT переопределяет ключевое слово TOP инструкции SELECT, если параметр ROWCOUNT имеет меньшее значение.  
  
 Значение параметра ROWCOUNT устанавливается во время выполнения, а не во время синтаксического анализа.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Инструкция SET ROWCOUNT завершает обработку после указанного числа строк. В следующем примере обратите внимание на то, что более 500 строк удовлетворяют условию: значение столбца `Quantity` меньше `300`. Однако после применения SET ROWCOUNT возвращаются не все строки.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Count`  
  
 `-----------`  
  
 `537`  
  
 `(1 row(s) affected)`  
  
 Теперь сделайте `ROWCOUNT` равным `4` и верните все строки, чтобы показать, что возвращается только 4 строки.  
  
```  
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 `(4 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Инструкция SET ROWCOUNT завершает обработку после указанного числа строк. В следующем примере обратите внимание на то, что более чем 20 строк отвечают критериям этого `AccountType = 'Assets'`. Однако после применения SET ROWCOUNT возвращаются не все строки.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 Чтобы вернуть все строки, set ROWCOUNT 0.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  



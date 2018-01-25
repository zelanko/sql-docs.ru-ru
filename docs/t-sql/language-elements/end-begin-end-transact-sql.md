---
title: "END (BEGIN... END) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- END
- END_TSQL
dev_langs: TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- END keyword
- BEGIN...END keyword
- END (BEGIN...END) keyword
ms.assetid: 354c4935-1375-4141-8195-61326662f4d2
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8bfe49b51578452a75dc1cf49746fe5d886c939
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="end-beginend-transact-sql"></a>Операторы END (BEGIN...END) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит серии инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], выполняемых как группа. Блоки BEGIN...END могут быть вложенными.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
BEGIN   
     { sql_statement | statement_block }   
END   
```  
  
## <a name="arguments"></a>Аргументы  
 { *sql_statement*| *statement_block*}  
 Любая допустимая инструкция или группа инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], определенных блоком инструкций. Чтобы определить блок инструкций (пакет), используются ключевые слова BEGIN и END языка управления выполнением. Несмотря на то что все [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы допустимы в пределах блока BEGIN... ОКОНЧАНИЯ блокировки, определенные [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции не должны быть сгруппированы вместе в пределах одного пакета (блока инструкций).  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере `BEGIN` и `END` определите ряд [!INCLUDE[DWsql](../../includes/dwsql-md.md)] инструкций, запускаемых одновременно. Если `BEGIN...END` блок не включаются, приведенный ниже будет непрерывно.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [BEGIN... КОНЕЦ &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ELSE &#40; Если... ELSE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md)   
 [IF... ELSE &#40; Transact-SQL &#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  



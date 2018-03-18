---
title: "SET STATISTICS TIME (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_TIME_TSQL
- SET STATISTICS TIME
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- time [SQL Server], statement processing statistics
- SET STATISTICS TIME statement
- STATISTICS TIME option
- statements [SQL Server], statistical information
- parsing [SQL Server], SET STATISTICS TIME statement
- compile times [SQL Server]
- execution processing time [SQL Server]
ms.assetid: eec2e1cd-a29d-4cf3-a271-be9d61506f15
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 523227164984cdabcb65afa3b9213c1cb0d0f18e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-statistics-time-transact-sql"></a>SET STATISTICS TIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отображает время в миллисекундах, необходимое для синтаксического анализа, компиляции и выполнения каждой инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET STATISTICS TIME { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 После выполнения инструкции SET STATISTICS TIME ON отображается статистика по времени для инструкций. Если указан параметр OFF, статистика по времени не показывается.  
  
 Значение параметра STATISTICS TIME устанавливается во время выполнения или запуска, а не во время синтаксического анализа.  
  
 В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] невозможно предоставить точную статистику в режиме волокон, который активируется при включении параметра конфигурации **использование упрощенных пулов**.  
  
 Столбец **cpu** в таблице **sysprocesses** обновляется только во время выполнения запроса с инструкцией SET STATISTICS TIME ON. Если для параметра SET STATISTICS TIME установлено значение OFF, возвращается значение **0**.  
  
 Настройки ON и OFF влияют на значения в столбце «ЦП» в окне «Просмотр сведений о процессах для текущей деятельности» в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Для использования инструкции SET STATISTICS TIME пользователи должны иметь разрешения, необходимые для выполнения инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Разрешение SHOWPLAN не требуется.  
  
## <a name="examples"></a>Примеры  
 В данном примере показано время выполнения, синтаксического анализа и компиляции сервера.  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS TIME ON;  
GO  
SELECT ProductID, StartDate, EndDate, StandardCost   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS TIME OFF;  
GO  
```  
  
 Результирующий набор:  
  
```  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
(269 row(s) affected)  
  
SQL Server Execution Times:  
   CPU time = 0 ms,  elapsed time = 2 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET STATISTICS IO (Transact-SQL)](../../t-sql/statements/set-statistics-io-transact-sql.md)  
  
  

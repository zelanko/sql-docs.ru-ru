---
title: "SET FMTONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FMTONLY_TSQL
- FMTONLY
- SET FMTONLY
- SET_FMTONLY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- metadata [SQL Server], only metadata returned
- SET FMTONLY statement
- FMTONLY option
ms.assetid: 02a1d9ac-2e58-433c-9a07-2c5a4a2214e1
caps.latest.revision: "48"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38625e3079956032513bb0e26c5d37b9a7071fea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-fmtonly-transact-sql"></a>SET FMTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает клиенту только метаданные. Может использоваться для тестирования формата ответа без фактического выполнения запроса.  
  
> [!NOTE]  
>  Не используйте эту функцию. Эта возможность была заменена [sp_describe_first_result_set &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md), [sp_describe_undeclared_parameters &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md), [sys.dm_exec_describe_first_result_set &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md), и [sys.dm_exec_describe_first_result_set_for_object &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET FMTONLY { ON | OFF }   
```  
  
## <a name="remarks"></a>Замечания  
 В результате запроса не было обработано или отправлено клиенту ни одной строки, так как параметр FMTONLY установлен в ON (инструкцией SET FMTONLY ON).  
  
 Инструкция SET FMTONLY относится ко времени выполнения, а не ко времени синтаксического анализа.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>Ответ, просмотрите сведения о заголовке столбца для запроса без фактического выполнения запроса.  
 В следующем примере состояние параметра `SET FMTONLY` изменяется на `ON`, после чего выполняется инструкция `SELECT`. В результате этой настройки инструкция возвращает только сведения о столбце; строки с данными не возвращаются.  
  
```  
USE AdventureWorks2012;  
GO  
SET FMTONLY ON;  
GO  
SELECT *   
FROM HumanResources.Employee;  
GO  
SET FMTONLY OFF;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>Б. Просмотрите сведения о заголовке столбца для запроса без фактического выполнения запроса.  
 Приведенный ниже показано, как возвращать сведения только об столбца заголовок (метаданные) для запроса. Пакет начинается с FMTONLY установлен в OFF и примет вид FMTONLY ON перед инструкцией SELECT. В результате инструкции SELECT для возврата только заголовки столбцов; строки данных, не возвращаются.  
  
```  
-- Uses AdventureWorks  
  
BEGIN  
    SET FMTONLY OFF;  
    SET DATEFORMAT mdy;  
    SET FMTONLY ON;  
    SELECT * FROM dbo.DimCustomer;  
    SET FMTONLY OFF;  
END  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


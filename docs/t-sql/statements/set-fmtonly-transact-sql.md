---
title: SET FMTONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FMTONLY_TSQL
- FMTONLY
- SET FMTONLY
- SET_FMTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], only metadata returned
- SET FMTONLY statement
- FMTONLY option
ms.assetid: 02a1d9ac-2e58-433c-9a07-2c5a4a2214e1
caps.latest.revision: 48
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 559edc2c3798529fda48930483e950fe79145791
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43068627"
---
# <a name="set-fmtonly-transact-sql"></a>SET FMTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает клиенту только метаданные. Может использоваться для тестирования формата ответа без фактического выполнения запроса.  
  
> [!NOTE]  
>  Не используйте эту функцию. Эта функция была заменена на [sp_describe_first_result_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md), [sp_describe_undeclared_parameters (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md), [sys.dm_exec_describe_first_result_set (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md) и [sys.dm_exec_describe_first_result_set_for_object (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET FMTONLY { ON | OFF }   
```  
  
## <a name="remarks"></a>Remarks  
 В результате запроса не было обработано или отправлено клиенту ни одной строки, так как параметр FMTONLY установлен в ON (инструкцией SET FMTONLY ON).  
  
 Инструкция SET FMTONLY относится ко времени выполнения, а не ко времени синтаксического анализа.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>А. Просмотр сведений о заголовке столбца для запроса без фактического выполнения запроса.  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-view-the-column-header-information-for-a-query-without-actually-running-the-query"></a>Б. Просмотр сведений о заголовке столбца для запроса без фактического выполнения запроса.  
 В следующем примере показано, как возвращать только сведения о столбце заголовка (метаданные) для запроса. Пакет начинается с FMTONLY с заданным значением OFF, и перед выполнением инструкции SELECT значение FMTONLY меняется на ON. В результате инструкция SELECT возвращает только заголовки столбцов; строки с данными не возвращаются.  
  
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
  
  


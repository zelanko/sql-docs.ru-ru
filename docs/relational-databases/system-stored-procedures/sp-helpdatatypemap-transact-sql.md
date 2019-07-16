---
title: sp_helpdatatypemap (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee304c9847019b21f1e08f57a3e0fdf0b439d241
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101400"
---
# <a name="sphelpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о сопоставления типов данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных системы управления (СУБД). Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_dbms = ] 'source_dbms'` — Имя СУБД, из которой сопоставляются типы данных. *source_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Источником является база данных Oracle.|  
  
`[ @source_version = ] 'source_version'` Версия продукта исходной СУБД. *source_version*— **varchar(10)** , и если не указан, сопоставления типов данных для всех версий исходной СУБД возвращаются. Позволяет фильтровать результирующий набор по типу данных по версии исходной СУБД.  
  
`[ @source_type = ] 'source_type'` Тип данных, приведенных в СУБД-источнике. *source_type* — **sysname**, и если не указан, возвращаются сопоставления для всех типов данных в исходной СУБД. Позволяет фильтровать результирующий набор по типу данных исходной СУБД.  
  
`[ @destination_dbms = ] 'destination_dbms'` — Имя целевой СУБД. *destination_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
  
`[ @destination_version = ] 'destination_version'` Версия продукта целевой СУБД. *destination_version*— **varchar(10)** , и если не указан, возвращаются сопоставления для всех версий целевой СУБД. Позволяет фильтровать результирующий набор по типу данных по версии целевой СУБД.  
  
`[ @destination_type = ] 'destination_type'` Тип данных, приведенных в целевой СУБД. *destination_type*— **sysname**, и если не указан, возвращаются сопоставления для всех типов данных в целевой СУБД. Позволяет фильтровать результирующий набор по типу данных целевой СУБД.  
  
`[ @defaults_only = ] defaults_only` — Если возвращаются только сопоставления типов данных по умолчанию. *defaults_only* — **бит**, значение по умолчанию **0**. **1** означает, что сопоставления типов только данные по умолчанию возвращаются. **0** означает, что чтобы сопоставления типов по умолчанию и пользовательские данные возвращаются.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**mapping_id**|Идентифицирует сопоставление типа данных.|  
|**source_dbms**|Название и номер версии исходной СУБД.|  
|**source_type**|Тип данных в исходной СУБД.|  
|**destination_dbms**|Название целевой СУБД.|  
|**destination_type**|Тип данных в целевой СУБД.|  
|**is_default**|Является ли сопоставление сопоставлением по умолчанию или альтернативным. Значение **0** указывает, что такое сопоставление определяется пользователем.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpdatatypemap** определяет сопоставление типа данных как из издателей, отличных от SQL Server, так и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей отличное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
 Если указанное сочетание исходной и целевой СУБД не поддерживается, **sp_helpdatatypemap** возвращает пустой результирующий набор.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе или члены **db_owner** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_helpdatatypemap**.  
  
## <a name="see-also"></a>См. также  
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  

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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61229514cb837a40537b6a363d2ebba81a5cef5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786869"
---
# <a name="sp_helpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает сведения об определенных сопоставлениях типов данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и системами управления, не являющимися [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] БАЗАМИ данных (СУБД). Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
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
`[ @source_dbms = ] 'source_dbms'`Имя СУБД, с которой сопоставляются типы данных. Аргумент *source_dbms* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Применение|Описание:|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Источником является база данных Oracle.|  
  
`[ @source_version = ] 'source_version'`Версия продукта исходной СУБД. *source_version*имеет тип **varchar (10)**, и если он не указан, возвращаются сопоставления типов данных для всех версий исходной СУБД. Позволяет фильтровать результирующий набор по типу данных по версии исходной СУБД.  
  
`[ @source_type = ] 'source_type'`Тип данных, указанный в исходной СУБД. Аргумент *source_type* имеет тип **sysname**, и если он не указан, то возвращаются сопоставления для всех типов данных в исходной СУБД. Позволяет фильтровать результирующий набор по типу данных исходной СУБД.  
  
`[ @destination_dbms = ] 'destination_dbms'`Имя целевой СУБД. Аргумент *destination_dbms* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Применение|Описание:|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
  
`[ @destination_version = ] 'destination_version'`Версия продукта целевой СУБД. *destination_version*имеет тип **varchar (10)**, и если он не указан, то возвращаются сопоставления для всех версий целевой СУБД. Позволяет фильтровать результирующий набор по типу данных по версии целевой СУБД.  
  
`[ @destination_type = ] 'destination_type'`Тип данных, указанный в целевой СУБД. Аргумент *destination_type*имеет тип **sysname**, и если он не указан, то возвращаются сопоставления для всех типов данных в целевой СУБД. Позволяет фильтровать результирующий набор по типу данных целевой СУБД.  
  
`[ @defaults_only = ] defaults_only`Имеет значение, если возвращаются только сопоставления типов данных по умолчанию. *defaults_only* имеет **бит**и значение по умолчанию **0**. **1** означает, что возвращаются только сопоставления типов данных по умолчанию. значение **0** означает, что возвращаются значения по умолчанию и любые пользовательские сопоставления типов данных.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**mapping_id**|Идентифицирует сопоставление типа данных.|  
|**source_dbms**|Название и номер версии исходной СУБД.|  
|**source_type**|Тип данных в исходной СУБД.|  
|**destination_dbms**|Название целевой СУБД.|  
|**destination_type**|Тип данных в целевой СУБД.|  
|**is_default**|Является ли сопоставление сопоставлением по умолчанию или альтернативным. Значение **0** указывает, что это сопоставление определяется пользователем.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpdatatypemap** определяет сопоставления типов данных как от издателей, отличных от SQL Server, так и от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей до подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если указанное сочетание исходной и целевой СУБД не поддерживается, **sp_helpdatatypemap** возвращает пустой результирующий набор.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе или члены предопределенной роли базы данных **db_owner** в базе данных распространителя могут выполнять **sp_helpdatatypemap**.  
  
## <a name="see-also"></a>См. также  
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  

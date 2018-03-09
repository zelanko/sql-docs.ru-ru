---
title: "sp_setdefaultdatatypemapping (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords:
- sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28b267b8e03fed032811aeaa98bbbf8b7c4b515c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spsetdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Помечает существующее сопоставление типов данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и значение, отличное от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных системы управления (СУБД) по умолчанию. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setdefaultdatatypemapping [ [ @mapping_id = ] mapping_id ]  
    [ , [ @source_dbms = ] 'source_dbms' ]  
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @source_length_min = ] source_length_min ]  
    [ , [ @source_length_max = ] source_length_max ]  
    [ , [ @source_precision_min = ] source_precision_min ]  
    [ , [ @source_precision_max = ] source_precision_max ]  
    [ , [ @source_scale_min = ] source_scale_min ]  
    [ , [ @source_scale_max = ] source_scale_max ]  
    [ , [ @source_nullable = ] source_nullable ]  
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @destination_length = ] destination_length ]  
    [ , [ @destination_precision = ] destination_precision ]  
    [ , [ @destination_scale = ] destination_scale ]  
    [ , [ @destination_nullable = ] source_nullable ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@mapping_id=** ] *mapping_id*  
 Идентифицирует сопоставление типа данных.  *mapping_id* — **int**, и значение по умолчанию NULL. При указании *mapping_id*, а затем остальные параметры не требуются.  
  
 [  **@source_dbms** =] **"***source_dbms***"**  
 Это имя СУБД, с которой сопоставлены типы данных. *source_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Источником является база данных Oracle.|  
|NULL (по умолчанию)||  
  
 Этот параметр обязателен, если *mapping_id* имеет значение NULL.  
  
 [  **@source_version=** ] **"***source_version***"**  
 Номер версии исходной СУБД. *source_version* — **varchar(10)**, значение по умолчанию NULL.  
  
 [  **@source_type** =] **"***source_type***"**  
 Тип данных в исходной СУБД. *source_type* — **sysname**. Этот параметр обязателен, если *mapping_id* имеет значение NULL.  
  
 [  **@source_length_min=** ] *source_length_min*  
 Минимальная длина типа данных в исходной СУБД. *source_length_min* — **bigint**, значение по умолчанию NULL.  
  
 [  **@source_length_max=** ] *source_length_max*  
 Максимальная длина типа данных в исходной СУБД. *source_length_max* — **bigint**, значение по умолчанию NULL.  
  
 [  **@source_precision_min=** ] *source_precision_min*  
 Минимальная точность типа данных в исходной СУБД. *source_precision_min* — **bigint**, значение по умолчанию NULL.  
  
 [  **@source_precision_max=** ] *source_precision_max*  
 Максимальная точность типа данных в исходной СУБД. *source_precision_max* — **bigint**, значение по умолчанию NULL.  
  
 [  **@source_scale_min=** ] *source_scale_min*  
 Минимальный масштаб типа данных в исходной СУБД. *source_scale_min* — **int**, значение по умолчанию NULL.  
  
 [  **@source_scale_max=** ] *source_scale_max*  
 Максимальный масштаб типа данных в исходной СУБД. *source_scale_max* — **int**, значение по умолчанию NULL.  
  
 [  **@source_nullable=** ] *source_nullable*  
 Показывает, что тип данных в исходной СУБД поддерживает значение NULL. *source_nullable* — **бит**, значение по умолчанию NULL. **1** означает, что значения NULL поддерживаются.  
  
 [  **@destination_dbms**  =] **"***destination_dbms***"**  
 Название целевой СУБД. *destination_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
|NULL (по умолчанию)||  
  
 [  **@destination_version** =] **"***destination_version***"**  
 Версия продукта целевой СУБД. *destination_version* — **varchar(10)**, значение по умолчанию NULL.  
  
 [  **@destination_type** =] **"***destination_type***"**  
 Тип данных, приведенных в списке целевой СУБД. *destination_type* — **sysname**, значение по умолчанию NULL.  
  
 [  **@destination_length=** ] *destination_length*  
 Длина типа данных в целевой СУБД. *destination_length* — **bigint**, значение по умолчанию NULL.  
  
 [  **@destination_precision=** ] *destination_precision*  
 Точность типа данных в целевой СУБД. *destination_precision* — **bigint**, значение по умолчанию NULL.  
  
 [  **@destination_scale=** ] *destination_scale*  
 Масштаб типа данных в целевой СУБД. *destination_scale* — **int**, значение по умолчанию NULL.  
  
 [  **@destination_nullable=** ] *destination_nullable*  
 Показывает, что тип данных в целевой СУБД поддерживает значение NULL. *destination_nullable* — **бит**, значение по умолчанию NULL. **1** означает, что значения NULL поддерживаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_setdefaultdatatypemapping** используется во всех типах репликации между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и значение, отличное от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] СУБД.  
  
 Сопоставления типов данных по умолчанию применяются ко всем топологиям репликации, включенным в указанную СУБД.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>См. также:  
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  

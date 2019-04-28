---
title: sp_setdefaultdatatypemapping (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords:
- sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e7d3ee86844f2b120c69e2cc2ddef55644cce8f2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62714351"
---
# <a name="spsetdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Помечает существующее сопоставление типов данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отличным от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных системы управления (СУБД) по умолчанию. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
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
`[ @mapping_id = ] mapping_id` Идентифицирует сопоставление типа данных.  *mapping_id* — **int**, значение по умолчанию NULL. Если указать *mapping_id*, а затем остальные параметры не требуются.  
  
`[ @source_dbms = ] 'source_dbms'` — Имя СУБД, из которой сопоставляются типы данных. *source_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Источником является база данных Oracle.|  
|NULL (по умолчанию)||  
  
 Этот параметр обязателен, если *mapping_id* имеет значение NULL.  
  
`[ @source_version = ] 'source_version'` — Номер версии исходной СУБД. *source_version* — **varchar(10)**, со значением по умолчанию NULL.  
  
`[ @source_type = ] 'source_type'` — Тип данных в исходной СУБД. *source_type* — **sysname**. Этот параметр обязателен, если *mapping_id* имеет значение NULL.  
  
`[ @source_length_min = ] source_length_min` — Это минимальная длина типа данных в исходной СУБД. *source_length_min* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_length_max = ] source_length_max` — Это максимальная длина типа данных в исходной СУБД. *source_length_max* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_precision_min = ] source_precision_min` — Это Минимальная точность типа данных в исходной СУБД. *source_precision_min* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_precision_max = ] source_precision_max` — Это максимальная точность типа данных в исходной СУБД. *source_precision_max* — **bigint**, со значением по умолчанию NULL.  
  
`[ @source_scale_min = ] source_scale_min` Это Минимальный масштаб типа данных в исходной СУБД. *source_scale_min* — **int**, со значением по умолчанию NULL.  
  
`[ @source_scale_max = ] source_scale_max` — Это максимальный масштаб типа данных в исходной СУБД. *source_scale_max* — **int**, со значением по умолчанию NULL.  
  
`[ @source_nullable = ] source_nullable` Показывает тип данных в исходной СУБД поддерживает значение NULL. *source_nullable* — **бит**, со значением по умолчанию NULL. **1** означает, что значения NULL допустимы.  
  
`[ @destination_dbms = ] 'destination_dbms'` — Имя целевой СУБД. *destination_dbms* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
|NULL (по умолчанию)||  
  
`[ @destination_version = ] 'destination_version'` Версия продукта целевой СУБД. *destination_version* — **varchar(10)**, со значением по умолчанию NULL.  
  
`[ @destination_type = ] 'destination_type'` Тип данных, приведенных в целевой СУБД. *destination_type* — **sysname**, со значением по умолчанию NULL.  
  
`[ @destination_length = ] destination_length` — Длина типа данных в целевой СУБД. *destination_length* — **bigint**, со значением по умолчанию NULL.  
  
`[ @destination_precision = ] destination_precision` — Это точность типа данных в целевой СУБД. *destination_precision* — **bigint**, со значением по умолчанию NULL.  
  
`[ @destination_scale = ] destination_scale` Является масштаб типа данных в целевой СУБД. *destination_scale* — **int**, со значением по умолчанию NULL.  
  
`[ @destination_nullable = ] destination_nullable` Показывает тип данных в целевой СУБД поддерживает значение NULL. *destination_nullable* — **бит**, со значением по умолчанию NULL. **1** означает, что значения NULL допустимы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_setdefaultdatatypemapping** используется во всех типах репликации между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отличным от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] СУБД.  
  
 Сопоставления типов данных по умолчанию применяются ко всем топологиям репликации, включенным в указанную СУБД.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>См. также  
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  

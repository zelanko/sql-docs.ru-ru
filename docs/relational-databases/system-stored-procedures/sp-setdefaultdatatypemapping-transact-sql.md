---
description: sp_setdefaultdatatypemapping (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6a712ecb629090947b0612844ce6049540b7359a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534959"
---
# <a name="sp_setdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Помечает существующее сопоставление типа данных между [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системой управления БАЗАМИ данных (СУБД) по умолчанию. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
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
`[ @mapping_id = ] mapping_id` Определяет сопоставление существующего типа данных.  *mapping_id* имеет **тип int**и значение по умолчанию NULL. Если указать *mapping_id*, остальные параметры не требуются.  
  
`[ @source_dbms = ] 'source_dbms'` Имя СУБД, с которой сопоставляются типы данных. Аргумент *source_dbms* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Источником является база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Источником является база данных Oracle.|  
|NULL (по умолчанию)||  
  
 Этот параметр необходимо указать, если *mapping_id* имеет значение null.  
  
`[ @source_version = ] 'source_version'` Номер версии исходной СУБД. *source_version* имеет тип **varchar (10)** и значение по умолчанию NULL.  
  
`[ @source_type = ] 'source_type'` Тип данных в исходной СУБД. *source_type* имеет тип **sysname**. Этот параметр необходимо указать, если *mapping_id* имеет значение null.  
  
`[ @source_length_min = ] source_length_min` Минимальная длина типа данных в исходной СУБД. *source_length_min* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @source_length_max = ] source_length_max` Максимальная длина типа данных в исходной СУБД. *source_length_max* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @source_precision_min = ] source_precision_min` Минимальная точность типа данных в исходной СУБД. *source_precision_min* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @source_precision_max = ] source_precision_max` Максимальная точность типа данных в исходной СУБД. *source_precision_max* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @source_scale_min = ] source_scale_min` Минимальный масштаб типа данных в исходной СУБД. *source_scale_min* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @source_scale_max = ] source_scale_max` Максимальный масштаб типа данных в исходной СУБД. *source_scale_max* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @source_nullable = ] source_nullable` Если тип данных в исходной СУБД поддерживает значение NULL. *source_nullable* имеет **бит**и значение по умолчанию NULL. **1** означает, что значения NULL поддерживаются.  
  
`[ @destination_dbms = ] 'destination_dbms'` Имя целевой СУБД. Аргумент *destination_dbms* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**MSSQLSERVER**|Целевая база данных — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**СУБД**|Целевой является база данных Oracle.|  
|**DB2**|Целевой является база данных IBM DB2.|  
|**SYBASE**|Целевой является база данных Sybase.|  
|NULL (по умолчанию)||  
  
`[ @destination_version = ] 'destination_version'` Версия продукта целевой СУБД. *destination_version* имеет тип **varchar (10)** и значение по умолчанию NULL.  
  
`[ @destination_type = ] 'destination_type'` Тип данных, указанный в целевой СУБД. Аргумент *destination_type* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @destination_length = ] destination_length` Длина типа данных в целевой СУБД. *destination_length* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @destination_precision = ] destination_precision` Точность типа данных в целевой СУБД. *destination_precision* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @destination_scale = ] destination_scale` Масштаб типа данных в целевой СУБД. *destination_scale* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @destination_nullable = ] destination_nullable` Если тип данных в целевой СУБД поддерживает значение NULL. *destination_nullable* имеет **бит**и значение по умолчанию NULL. **1** означает, что значения NULL поддерживаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_setdefaultdatatypemapping** используется во всех типах репликации между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] СУБД.  
  
 Сопоставления типов данных по умолчанию применяются ко всем топологиям репликации, включенным в указанную СУБД.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>См. также  
 [Указание сопоставлений типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  

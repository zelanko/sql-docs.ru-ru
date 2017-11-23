---
title: "sys.sp_add_trusted_assembly (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs: TSQL
helpviewer_keywords: sys.sp_add_trusted_assembly
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan;rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91cedb6c140b9f969d1d33e4878788fa8b9dba92
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysspaddtrustedassembly-transact-sql"></a>sys.sp_add_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Добавляет сборку в список доверенных сборок для сервера.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Синтаксис
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>Замечания  

Эта процедура добавляет сборку [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).

## <a name="arguments"></a>Аргументы

[ @hash =] '*значение*"  
Хэш-значение SHA2_512 сборки, которую необходимо добавить в список доверенных сборок для сервера. Доверенные сборки могут загружаться при [строгой безопасности CLR](../../database-engine/configure-windows/clr-strict-security.md) включена, даже если сборка не подписана или база данных не помечена как заслуживающая доверия.

[ @description =] '*описание*"  
Необязательное пользовательское описание сборки. Корпорация Майкрософт рекомендует использовать каноническое имя, кодирующая простое имя, номер версии, язык и региональные параметры, открытый ключ и архитектуру сборки для доверия. Это значение уникально идентифицирует сборку среды выполнения (CLR) стороны выполнения и совпадает со значением clr_name значение sys.assemblies. 

## <a name="permissions"></a>Permissions

Требуется членство в `sysadmin` предопределенной роли сервера или `CONTROL SERVER` разрешение.

## <a name="examples"></a>Примеры  

В следующем примере добавляется сборку с именем `pointudt` в список доверенных сборок для сервера. Эти значения доступны из [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md).     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>См. также:  
  [sys.sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  [Строгой безопасности среды CLR](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


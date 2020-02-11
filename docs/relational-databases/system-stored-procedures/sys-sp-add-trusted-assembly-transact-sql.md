---
title: sys. sp_add_trusted_assembly (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_add_trusted_assembly
ms.assetid: ''
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb34a814780a46c12c65948bd0b552effaacda4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72452869"
---
# <a name="syssp_add_trusted_assembly-transact-sql"></a>sys.sp_add_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdbmi-xxxx-xxx-md.md)]

Добавляет сборку в список доверенных сборок для сервера.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Синтаксис
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>Remarks  

Эта процедура добавляет сборку в [sys. trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).

## <a name="arguments"></a>Аргументы

[ @hash = ] "*значение*"  
SHA2_512 хэш-значение сборки, добавляемой в список доверенных сборок для сервера. Доверенные сборки могут загружаться, когда включена [строгая безопасность CLR](../../database-engine/configure-windows/clr-strict-security.md) , даже если сборка не подписана или база данных не помечена как заслуживающая доверия.

[ @description = ] "*Описание*"  
Необязательное описание сборки, определяемое пользователем. Корпорация Майкрософт рекомендует использовать каноническое имя, которое кодирует простое имя, номер версии, язык и региональные параметры, Открытый ключ и архитектуру сборки для отношения доверия. Это значение однозначно определяет сборку на стороне среды CLR и совпадает со значением clr_name в sys. assemblies. 

## <a name="permissions"></a>Разрешения

Требуется членство в `sysadmin` предопределенной роли сервера `CONTROL SERVER` или в разрешении.

## <a name="examples"></a>Примеры  

В следующем примере в список доверенных `pointudt` сборок для сервера добавляется сборка с именем. Эти значения доступны из представления [sys. assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md).     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>См. также:  
  [sys. sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys. trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [Создание сборки &#40;&#41;Transact-SQL](../../t-sql/statements/create-assembly-transact-sql.md)  
  [Среда CLR с уровнем безопасности](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


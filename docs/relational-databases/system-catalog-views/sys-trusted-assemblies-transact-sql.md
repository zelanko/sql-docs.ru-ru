---
title: sys.trusted_assemblies (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: ''
caps.latest.revision: ''
author: tmullaney
ms.author: thmullan
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 80fd8a091aa04d0574da5c5a2377628b2e8c376a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Содержит по одной строке для каждой сборки, доверенным для сервера.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Имя столбца |Тип данных |Описание |
|--- |--- |--- |
|Хэш |varbinary(8000) |SHA2_512 хэш содержимого сборки. |
|description |nvarchar(4000) |Необязательное пользовательское описание сборки. Корпорация Майкрософт рекомендует использовать каноническое имя, кодирующая простое имя, номер версии, язык и региональные параметры, открытый ключ и архитектуру сборки для доверия. Это значение уникально идентифицирует сборку среды выполнения (CLR) стороны выполнения и совпадает со значением clr_name значение sys.assemblies. |
|create_date |datetime2 |Дата добавления сборки в список доверенных сборок. |
|created_by |nvarchar(128) |Имя входа участника, которому добавляется к списку сборки. |
| | | |


## <a name="remarks"></a>Замечания  

Используйте **необходимо добавить sp_add_trusted_assembly** и **необходимо добавить sys.trusted_assemblies** добавить или удалить сборки из `sys.trusted_assemblies`.

## <a name="see-also"></a>См. также  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


---
description: sys.trusted_assemblies (Transact-SQL)
title: sys.trusted_assemblies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f6d3305687b7592d8503911e9385cd04a93f16a4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97428393"
---
# <a name="systrusted_assemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[SQL Server 2017](../../includes/applies-to-version/sqlserver2017.md)]

Содержит по одной строке для каждой доверенной сборки сервера.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Имя столбца |Тип данных |Описание |
|--- |--- |--- |
|hash |varbinary(8000) |SHA2_512 хэш содержимого сборки. |
|description |nvarchar(4000) |Необязательное описание сборки, определяемое пользователем. Корпорация Майкрософт рекомендует использовать каноническое имя, которое кодирует простое имя, номер версии, язык и региональные параметры, Открытый ключ и архитектуру сборки для отношения доверия. Это значение однозначно определяет сборку на стороне среды CLR и совпадает со значением clr_name в sys. assemblies. |
|create_date |datetime2 |Дата добавления сборки в список доверенных сборок. |
|created_by |NVARCHAR(128) |Имя входа участника, который добавил сборку в список. |
| | | |

### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
 
## <a name="remarks"></a>Комментарии  
Используйте **[sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)** для добавления и **[sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)** для удаления сборок из `sys.trusted_assemblies` .

## <a name="see-also"></a>См. также:  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)  
  [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)  
  [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

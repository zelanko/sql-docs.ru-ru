---
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
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9682535c82f8a579259993e82560dfe6bc930f93
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061366"
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Содержит по строке для каждой сборки, доверенным для сервера.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Имя столбца |Тип данных |Описание |
|--- |--- |--- |
|Хэш |varbinary(8000) |SHA2_512 хэш содержимого сборки. |
|description |nvarchar(4000) |Необязательное пользовательское описание сборки. Корпорация Майкрософт рекомендует использовать каноническое имя, кодирующая простое имя, номер версии, язык и региональные параметры, открытый ключ и архитектуру сборки для доверия. Это значение уникально идентифицирует сборку среды выполнения (CLR) стороны выполнения и совпадает со значением значение clr_name sys.assemblies. |
|create_date |datetime2 |Дата, когда сборка была добавлена в список доверенных сборок. |
|created_by |NVARCHAR(128) |Имя входа участника, добавляемого в список сборки. |
| | | |


## <a name="remarks"></a>Примечания  

Используйте **нужно добавить sp_add_trusted_assembly** и **нужно добавить sys.trusted_assemblies** добавить или удалить сборки из `sys.trusted_assemblies`.

## <a name="see-also"></a>См. также  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [инструкция DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


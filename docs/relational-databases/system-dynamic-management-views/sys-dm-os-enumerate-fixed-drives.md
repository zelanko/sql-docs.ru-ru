---
title: sys. dm_os_enumerate_fixed_drives (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/18/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_enumerate_fixed_drives
- sys.dm_os_enumerate_fixed_drives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_enumerate_fixed_drives dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fa5834c14bfb1fafe3123c28a60359d64d059dfc
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342519"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>sys. dm_os_enumerate_fixed_drives (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Введено в SQL Server 2019.

Перечисляет тома, подключенные к буквам диска, например `C:\`.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|Путь к тому, например `C:\`.|  
|`drive_type`|`int`|Код для типа диска. См. раздел [функция`GetDriveTypeW`](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`drive_type_desc`|`nvarchar(512)`|Описание типа диска. См. раздел [функция`GetDriveTypeW`](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`free_space_in_bytes`|`bigint`|Свободное место на диске (в байтах).|

## <a name="permissions"></a>Разрешения

Пользователь должен иметь разрешение `VIEW SERVER STATE` на сервере.

## <a name="see-also"></a>См. также статью  

 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции &#40;, связанные с вводом-выводом. TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  

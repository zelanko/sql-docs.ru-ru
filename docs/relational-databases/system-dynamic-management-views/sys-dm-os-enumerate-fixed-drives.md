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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 827d044bc4601044cc805aea72c33723b0889d0b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754181"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>sys. dm_os_enumerate_fixed_drives (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

Введено в SQL Server 2019.

Перечисляет тома, подключенные к буквам диска `C:\` , например.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|Путь к тому, например `C:\` .|  
|`drive_type`|`int`|Код для типа диска. См. раздел [ `GetDriveTypeW` функция](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`drive_type_desc`|`nvarchar(512)`|Описание типа диска. См. раздел [ `GetDriveTypeW` функция](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`free_space_in_bytes`|`bigint`|Свободное место на диске (в байтах).|

## <a name="permissions"></a>Разрешения

Пользователь должен иметь `VIEW SERVER STATE` разрешение на сервере.

## <a name="see-also"></a>См. также  

 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с вводом-выводом &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  

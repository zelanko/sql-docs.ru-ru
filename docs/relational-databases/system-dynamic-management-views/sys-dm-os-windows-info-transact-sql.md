---
description: sys.dm_os_windows_info (Transact-SQL)
title: sys. dm_os_windows_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ba205fe097367dc273d22d49d54f51a31cedbbfc
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89531936"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает одну строку с информацией о версии операционной системы Windows.  
  
  Применяется только к SQL Server, работающему в Windows. Чтобы увидеть похожие информатон для SQL Server, выполняющихся на узле, отличном от Windows, например Linux, используйте представление [sys. dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Для Windows возвращает номер выпуска. Список значений и описаний см. в разделе [версия операционной системы (Windows)](/windows/desktop/SysInfo/operating-system-version). Не может быть NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Для Windows возвращает номер пакета обновления. Не может быть NULL. |  
|**windows_sku**|**int**|Для Windows возвращает идентификатор единицы хранения запасов Windows (SKU). Список идентификаторов SKU и их описание см. в разделе [функция жетпродуктинфо](https://msdn.microsoft.com/library/ms724358.aspx). Допускает значение null. |  
|**os_language_version**|**int**| Для Windows возвращает идентификатор локали Windows (LCID) операционной системы. Список значений и описаний LCID см. в разделе [идентификаторы языков, назначенные корпорацией Майкрософт](https://go.microsoft.com/fwlink/?LinkId=208080). Не может быть NULL.|  
  
  
## <a name="permissions"></a>Разрешения  
Разрешение SELECT на представление sys. dm_os_windows_info предоставляется по умолчанию для роли public. Если параметр отозван, требуется разрешение VIEW SERVER STATE на сервере.  

## <a name="limitations-and-restrictions"></a>Ограничения
Чтобы увидеть информатон for SQL, работающий на узле, отличном от Windows, например Linux, используйте представление [sys. dm_os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все столбцы из представления **sys. dm_os_windows_info** .  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 Ниже приводится образец результирующего набора.  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>См. также  
 [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  


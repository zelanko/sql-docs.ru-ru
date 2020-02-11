---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25713ba8fb298ce465910eae786befb710961d7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899585"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку с информацией о версии операционной системы Windows.  
  
  Применяется только к SQL Server, работающему в Windows. Чтобы увидеть похожие информатон для SQL Server, выполняющихся на узле, отличном от Windows, например Linux, используйте представление [sys. dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Имя столбца|Тип данных|Description|  
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
  
## <a name="see-also"></a>См. также:  
 [sys. dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  


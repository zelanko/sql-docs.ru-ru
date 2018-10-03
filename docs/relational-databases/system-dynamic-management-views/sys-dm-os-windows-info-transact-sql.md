---
title: sys.dm_os_windows_info (Transact-SQL) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: b61127c2844117b2d9c042b352129a1860e227c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743192"
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку с информацией о версии операционной системы Windows.  
  
  Применяется только к SQL Server на Windows. Чтобы просмотреть аналогичные сведения для SQL Server, запущенный на узле отличных от Windows, например Linux, используйте [sys.dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Для Windows возвращает номер выпуска. Список значений и описаний, см. в разделе [версии операционной системы (Windows)](/windows/desktop/SysInfo/operating-system-version). Не может быть NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Для Windows возвращает номер пакета обновления. Не может быть NULL. |  
|**windows_sku**|**int**|Для Windows возвращает идентификатор Windows Stock сохранение номер SKU. Список идентификаторов SKU и описания, см. в разделе [функция GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). Значение NULL. |  
|**os_language_version**|**int**| Для Windows возвращает идентификатор языкового стандарта Windows (LCID) операционной системы. Список значений LCID и описания, см. в разделе [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkId=208080). Не может быть NULL.|  
  
  
## <a name="permissions"></a>Разрешения  
По умолчанию разрешение SELECT на sys.dm_os_windows_info предоставляется роли public. Если отозван, требуется разрешение VIEW SERVER STATE на сервере.  

## <a name="limitations-and-restrictions"></a>Ограничения
Чтобы просмотреть сведения для SQL, работающие на узле отличных от Windows, например Linux, используйте [sys.dm_os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все столбцы из **sys.dm_os_windows_info** представления.  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 Ниже приводится образец результирующего набора.  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>См. также  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  


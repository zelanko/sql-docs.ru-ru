---
title: "sys.dm_os_windows_info (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 759ac050225bdc1abd78a6400152c6ee7f89dcfd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку с информацией о версии операционной системы Windows.  
  
  Применяется только к SQL Server, работающей под управлением Windows. Чтобы просмотреть аналогичные informaton для SQL Server, запущенный на узле не под управлением Windows, например в Linux, используйте [sys.dm_os_host_info &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Для Windows возвращает номер выпуска. Список значений и описания см. в разделе [версии операционной системы (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx). Не может быть NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Для Windows возвращает номер пакета обновления. Не может быть NULL. |  
|**windows_sku**|**int**|Для Windows возвращает идентификатор единицы хранения Stock Windows (SKU) Список идентификаторов SKU и описания см. в разделе [функция GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). Допускает значение NULL. |  
|**os_language_version**|**int**| Для Windows возвращает идентификатор языкового стандарта Windows (LCID) операционной системы. Список значений LCID и описания см. в разделе [языкового стандарта, назначаемые в Майкрософт](http://go.microsoft.com/fwlink/?LinkId=208080). Не может быть NULL.|  
  
  
## <a name="permissions"></a>Permissions  
По умолчанию разрешение SELECT на sys.dm_os_windows_info предоставляется роли public. Если отозван, требуется разрешение VIEW SERVER STATE на сервере.  

## <a name="limitations-and-restrictions"></a>Ограничения
Чтобы просмотреть informaton для SQL, выполняемыми на узле не под управлением Windows, например в Linux, используйте [sys.dm_os_host_info &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
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
  
## <a name="see-also"></a>См. также:  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  


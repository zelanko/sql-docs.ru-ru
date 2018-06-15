---
title: sys.dm_os_host_info (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0aa5f28f52c9d0df4e942809612e1ca59a1cb3c5
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463940"
---
# <a name="sysdmoshostinfo-transact-sql"></a>sys.dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает одну строку, которая отображает сведения о версии операционной системы.  
  
|Имя столбца |Тип данных |Описание |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Тип операционной системы: Windows или Linux |
|**host_distribution** |**nvarchar(256)** |Описание операционной системы. |
|**host_release**|**nvarchar(256)**|Выпуск операционной системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (номер версии). Список значений и описания см. в разделе [версии операционной системы (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx). <br> Для Linux возвращается пустая строка. |  
|**host_service_pack_level**|**nvarchar(256)**|Версия пакета обновления операционной системы Windows. <br> Для Linux возвращается пустая строка. |  
|**host_sku**|**int**|Идентификатор Windows SKU. Список идентификаторов SKU и описания см. в разделе [функция GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). Допускает значение NULL. <br> Для Linux возвращает значение NULL. |  
|**os_language_version**|**int**|Идентификатор локали (LCID) операционной системы Windows. Список значений LCID и описания см. в разделе [языкового стандарта, назначаемые в Майкрософт](http://go.microsoft.com/fwlink/?LinkId=208080). Не может иметь значение null.|  

## <a name="remarks"></a>Примечания  
Это представление похоже на [sys.dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), добавлению столбцов для различения Windows и Linux.
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
`SELECT` Разрешение на `sys.dm_os_host_info` предоставляется `public` роли по умолчанию. При запрете требуется `VIEW SERVER STATE` разрешение на сервере.   
 
>  [!CAUTION]
>  Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP-версии 1.3, [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] требуется версия 17 `SELECT` разрешение на `sys.dm_os_host_info` для подключения к [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Если `SELECT` отзывается разрешение `public`, только имена входа с `VIEW SERVER STATE` разрешений можно подключиться, используя последнюю версию SSMS. (Другие средства, такие как `sqlcmd.exe` можно подключиться без `SELECT` разрешение на `sys.dm_os_host_info`.)

  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все столбцы из **sys.dm_os_host_info** представления.  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Ниже приведен образец результирующего набора в Windows:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Ниже приведен образец результирующего набора в Linux:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>См. также  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 


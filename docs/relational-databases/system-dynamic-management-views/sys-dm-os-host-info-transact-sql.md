---
title: sys. dm_os_host_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 052402d3a394e8da3e08828992127d3cd89b95ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900167"
---
# <a name="sysdm_os_host_info-transact-sql"></a>sys. dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает одну строку, отображающую сведения о версии операционной системы.  
  
|Имя столбца |Тип данных |Description |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Тип операционной системы: Windows или Linux. |
|**host_distribution** |**nvarchar(256)** |Описание операционной системы. |
|**host_release**|**nvarchar(256)**|Выпуск операционной системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (номер версии). Список значений и описаний см. в разделе [версия операционной системы (Windows)](/windows/desktop/SysInfo/operating-system-version). <br> Для Linux возвращает пустую строку. |  
|**host_service_pack_level**|**nvarchar(256)**|Версия пакета обновления операционной системы Windows. <br> Для Linux возвращает пустую строку. |  
|**host_sku**|**int**|Идентификатор Windows SKU. Список идентификаторов SKU и их описание см. в разделе [функция жетпродуктинфо](https://msdn.microsoft.com/library/ms724358.aspx). Допускает значение NULL. <br> Для Linux возвращает значение NULL. |  
|**os_language_version**|**int**|Идентификатор локали (LCID) операционной системы Windows. Список значений и описаний LCID см. в разделе [идентификаторы языков, назначенные корпорацией Майкрософт](https://go.microsoft.com/fwlink/?LinkId=208080). Не может иметь значение null.|  

## <a name="remarks"></a>Remarks  
Это представление похоже на [sys. dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), добавляя столбцы для различения Windows и Linux.
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
По `SELECT` умолчанию `sys.dm_os_host_info` разрешение предоставляется `public` роли. Если параметр отозван, требуется `VIEW SERVER STATE` разрешение на сервере.   
 
> [!CAUTION]
>  Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1,3 для [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] подключения к [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `SELECT` разрешение `sys.dm_os_host_info` для версии 17. Если `SELECT` разрешение отменяется `public`, только имена входа с `VIEW SERVER STATE` разрешением могут подключаться к последней версии SSMS. (Другие средства, например, `sqlcmd.exe` могут подключаться `SELECT` без `sys.dm_os_host_info`разрешения на.)

  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все столбцы из представления **sys. dm_os_host_info** .  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Ниже приведен пример результирующего набора для Windows.
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Ниже приведен пример результирующего набора для Linux:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>См. также:  
 [sys. dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 


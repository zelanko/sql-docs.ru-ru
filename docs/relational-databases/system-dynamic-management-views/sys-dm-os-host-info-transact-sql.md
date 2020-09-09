---
description: sys. dm_os_host_info (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97d313e91fdd719a7ff33728bf3183980f564910
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550234"
---
# <a name="sysdm_os_host_info-transact-sql"></a>sys. dm_os_host_info (Transact-SQL)
[!INCLUDE[SQL Server 2017](../../includes/applies-to-version/sqlserver2017.md)]

Возвращает одну строку, отображающую сведения о версии операционной системы.  
  
|Имя столбца |Тип данных |Описание |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Тип операционной системы: Windows или Linux. |
|**host_distribution** |**nvarchar(256)** |Описание операционной системы. |
|**host_release**|**nvarchar(256)**|Выпуск операционной системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (номер версии). Список значений и описаний см. в разделе [версия операционной системы (Windows)](/windows/desktop/SysInfo/operating-system-version). <br> Для Linux возвращает пустую строку. |  
|**host_service_pack_level**|**nvarchar(256)**|Версия пакета обновления операционной системы Windows. <br> Для Linux возвращает пустую строку. |  
|**host_sku**|**int**|Идентификатор Windows SKU. Список идентификаторов SKU и их описание см. в разделе [функция жетпродуктинфо](https://msdn.microsoft.com/library/ms724358.aspx). Допускает значение NULL. <br> Для Linux возвращает значение NULL. |  
|**os_language_version**|**int**|Идентификатор локали (LCID) операционной системы Windows. Список значений и описаний LCID см. в разделе [идентификаторы языков, назначенные корпорацией Майкрософт](https://go.microsoft.com/fwlink/?LinkId=208080). Не может иметь значение NULL.|  

## <a name="remarks"></a>Примечания  
Это представление похоже на [sys. dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), добавляя столбцы для различения Windows и Linux.
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
По `SELECT` `sys.dm_os_host_info` `public` умолчанию разрешение предоставляется роли. Если параметр отозван, требуется `VIEW SERVER STATE` разрешение на сервере.   
 
> [!CAUTION]
>  Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1,3 для [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] подключения к необходимо разрешение для версии 17 `SELECT` `sys.dm_os_host_info` [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Если `SELECT` разрешение отменяется `public` , только имена входа с `VIEW SERVER STATE` разрешением могут подключаться к последней версии SSMS. (Другие средства, например, `sqlcmd.exe` могут подключаться без `SELECT` разрешения на `sys.dm_os_host_info` .)

  
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
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Ниже приведен пример результирующего набора для Linux:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>См. также  
 [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 


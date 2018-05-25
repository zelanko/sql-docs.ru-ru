---
title: sys.dm_server_services (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 427dfc77aaf7178a9bd14a7243be4a44a9e1781c
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о службах SQL Server, полнотекстового поиска и агента SQL Server в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это динамическое административное представление позволяет получить сведения о состоянии данных служб.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Имя [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Full-text или службы агента SQL Server. Не может иметь значение null.|  
|startup_type|**int**|Показывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 0: другие<br />1: другие<br />2: автоматический<br />3: вручную<br />4: отключено<br /><br /> Допускает значение NULL.|  
|startup_desc|**nvarchar(256)**|Описывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Другой: С другой (при загрузке ОС)<br />Другой: С другой (при запуске системы)<br />Автоматический: Автоматический запуск<br />Вручную: Требование на запуск<br />Отключено: отключено<br /><br /> Не может иметь значение null.|  
|status|**int**|Показывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 1: остановлена<br />2: других (ожидает запуска)<br />3: других (ждет остановки)<br />4: запуск<br />5: других (ждет продолжения)<br />6: другие (ждет приостановки)<br />7: приостановлено<br /><br /> Допускает значение NULL.|  
|status_desc|**nvarchar(256)**|Описывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Остановлена: Служба остановлена.<br />Другие (отложенный запуск): служба находится в процессе запуска.<br />Другие (отложенная остановка): служба находится в процессе остановки.<br />Выполнения: Служба запущена.<br />Другие (отложенное): служба находится в состоянии ожидания.<br />Другие (ждет приостановки): служба находится в процессе приостановки.<br />Приостановлено: Служба приостановлена.<br /><br /> Не может иметь значение null.|  
|process_id|**int**|Идентификатор процесса службы. Не может иметь значение null.|  
|last_startup_time|**datetimeoffset(7)**|Дата и время последнего запуска службы. Допускает значение NULL.|  
|service_account|**nvarchar(256)**|Учетная запись, имеющая право управлять этой службой. Данная учетная запись может запускать и останавливать службу или изменять ее свойства. Не может иметь значение null.|  
|filename|**nvarchar(256)**|Полный путь и имя исполняемого файла службы. Не может иметь значение null.|  
|is_clustered|**nvarchar(1)**|Указывает, установлена ли служба в качестве ресурса кластеризованного сервера. Не может иметь значение null.|  
|cluster_nodename|**nvarchar(256)**|Имя узла кластера, на котором установлена служба. Допускает значение NULL.|
|instant_file_initialization_enabled|**nvarchar(1)**|Указывает, включена ли мгновенную инициализацию файлов для [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] службы.<br /><br />Y = мгновенную инициализацию файлов включено для службы.<br /><br />N = мгновенную инициализацию файлов отключен для службы.<br /><br /> Допускает значение NULL.<br /><br /> **Примечание:** не применяется к другим службам, например агент SQL Server.<br /><br /> **Применяется к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 через через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  

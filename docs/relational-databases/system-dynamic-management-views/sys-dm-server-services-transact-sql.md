---
title: "sys.dm_server_services (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/28/2017
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
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8642cd9036fcaf7835c6dffc01f60817bdaa82bb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о службах SQL Server, полнотекстового поиска и агента SQL Server в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это динамическое административное представление позволяет получить сведения о состоянии данных служб.  
  
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Имя службы SQL Server, полнотекстового поиска или агента SQL Server. Не может иметь значение null.|  
|startup_type|**int**|Показывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 0: другие<br />1: другие<br />2: автоматический<br />3: вручную<br />4: отключено<br /><br /> Допускает значение NULL.|  
|startup_desc|**nvarchar(256)**|Описывает режим запуска службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Другой: С другой (при загрузке ОС)<br />Другой: С другой (при запуске системы)<br />Автоматический: Автоматический запуск<br />Вручную: Требование на запуск<br />Отключено: отключено<br /><br /> Не может иметь значение null.|  
|status|**int**|Показывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> 1: остановлена<br />2: других (ожидает запуска)<br />3: других (ждет остановки)<br />4: запуск<br />5: других (ждет продолжения)<br />6: другие (ждет приостановки)<br />7: приостановлено<br /><br /> Допускает значение NULL.|  
|status_desc|**nvarchar(256)**|Описывает текущее состояние службы. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Остановлена: Служба остановлена.<br />Другие (отложенный запуск): служба находится в процессе запуска.<br />Другие (отложенная остановка): служба находится в процессе остановки.<br />Выполнения: Служба запущена.<br />Другие (отложенное): служба находится в состоянии ожидания.<br />Другие (ждет приостановки): служба находится в процессе приостановки.<br />Приостановлено: Служба приостановлена.<br /><br /> Не может иметь значение null.|  
|process_id|**int**|Идентификатор процесса службы. Не может иметь значение null.|  
|last_startup_time|**DateTimeOffset(7)**|Дата и время последнего запуска службы. Допускает значение NULL.|  
|service_account|**nvarchar(256)**|Учетная запись, имеющая право управлять этой службой. Данная учетная запись может запускать и останавливать службу или изменять ее свойства. Не может иметь значение null.|  
|filename|**nvarchar(256)**|Полный путь и имя исполняемого файла службы. Не может иметь значение null.|  
|is_clustered|**nvarchar(1)**|Указывает, установлена ли служба в качестве ресурса кластеризованного сервера. Не может иметь значение null.|  
|cluster_nodename|**nvarchar(256)**|Имя узла кластера, на котором установлена служба. Допускает значение NULL.|
|instant_file_initialization_enabled|**nvarchar(1)**|**Применяется к: [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, а начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1**.<br /><br />Указывает, включен ли мгновенную инициализацию файлов для службы SQL Server Database Engine. Это свойство не применяется к службам (пример: агент SQL Server) кроме службы SQL Server Database Engine. допускает значения NULL.<br /><br />Y = мгновенную инициализацию файлов включено для службы.<br /><br />N = мгновенную инициализацию файлов отключен для службы.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_server_registry &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
  

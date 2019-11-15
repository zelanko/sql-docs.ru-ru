---
title: sys. dm_server_services (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: a480ba134a4f3049f7501cb68a0331ac8fdd386b
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095372"
---
# <a name="sysdm_server_services-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о SQL Server, полнотекстовом панель запуска SQL Server службе (SQL Server 2017 +) и службах агент SQL Server в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это динамическое административное представление позволяет получить сведения о состоянии данных служб.  
  
 
|Имя столбца|Data type|Описание|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Имя [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], полнотекстового или агент SQL Server службы. Не может иметь значение null.|  
|startup_type|**int**|Показывает режим запуска службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> 0: другое<br />1: другое<br />2: автоматически<br />3: вручную<br />4: отключено<br /><br /> Допускает значение NULL.|  
|startup_type_desc|**nvarchar(256)**|Описывает режим запуска службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> Другое: другое (загрузочный запуск)<br />Другие: другие (системный запуск)<br />Автоматически: автоматический запуск<br />Вручную: запуск по требованию<br />Отключено: отключено<br /><br /> Не может иметь значение null.|  
|status|**int**|Показывает текущее состояние службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> 1: остановлено<br />2: другое (ожидается запуск)<br />3: другое (ожидание ожидания)<br />4: работает<br />5: другое (ожидается продолжение)<br />6: другое (ожидание приостановки)<br />7: приостановлено<br /><br /> Допускает значение NULL.|  
|status_desc|**nvarchar(256)**|Описывает текущее состояние службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> Остановлено: служба остановлена.<br />Другое (ожидание операции запуска): служба находится в процессе запуска.<br />Другое (ожидание операции остановки): служба находится в процессе остановки.<br />Работает: служба запущена.<br />Другое (ожидается продолжение операций): служба находится в состоянии ожидания.<br />Другое (ожидание приостановки): служба находится в процессе приостановки.<br />Приостановлено: служба приостановлена.<br /><br /> Не может иметь значение null.|  
|process_id|**int**|Идентификатор процесса службы. Не может иметь значение null.|  
|last_startup_time|**datetimeoffset(7)**|Дата и время последнего запуска службы. Допускает значение NULL.|  
|service_account|**nvarchar(256)**|Учетная запись, имеющая право управлять этой службой. Данная учетная запись может запускать и останавливать службу или изменять ее свойства. Не может иметь значение null.|  
|filename|**nvarchar(256)**|Полный путь и имя исполняемого файла службы. Не может иметь значение null.|  
|is_clustered|**nvarchar (1)**|Указывает, установлена ли служба в качестве ресурса кластеризованного сервера. Не может иметь значение null.|  
|cluster_nodename|**nvarchar(256)**|Имя узла кластера, на котором установлена служба. Допускает значение NULL.|
|instant_file_initialization_enabled|**nvarchar (1)**|Указывает, включена ли Мгновенная инициализация файлов для службы [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].<br /><br />Y = Мгновенная инициализация файлов включена для службы.<br /><br />N = Мгновенная инициализация файлов отключена для службы.<br /><br /> Допускает значение NULL.<br /><br /> **Примечание.** Не применяется к другим службам, таким как агент SQL Server.<br /><br /> **Применимо к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) и более поздней версии).|  

## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также статью  
 [sys. dm_server_registry &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  

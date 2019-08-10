---
title: sys. DM _server_services (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: b1c44b269f68b39d633a18f366615fd41b582938
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892949"
---
# <a name="sysdm_server_services-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о службах SQL Server, полнотекстового поиска и агента SQL Server в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это динамическое административное представление позволяет получить сведения о состоянии данных служб.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|Имя службы, полнотекстового или агент SQL Server. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Не может иметь значение null.|  
|startup_type|**int**|Показывает режим запуска службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> 0: Другое<br />1: Другое<br />2: Автоматически<br />3: Вручную<br />4: Выключено<br /><br /> Допускает значение NULL.|  
|startup_type_desc|**nvarchar(256)**|Описывает режим запуска службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> Иной Другое (загрузочный запуск)<br />Иной Другое (системный запуск)<br />Автоматически: Автоматический запуск<br />Вручную: Запуск по требованию<br />Отключено: Выключено<br /><br /> Не может иметь значение null.|  
|status|**int**|Показывает текущее состояние службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> 1: Остановлена<br />2: Другое (ожидается запуск)<br />3: Другое (ожидание завершения)<br />4: Запущен<br />5: Другое (Ожидание продолжения)<br />1-6 Другое (ожидание приостановки)<br />7 Пауза<br /><br /> Допускает значение NULL.|  
|status_desc|**nvarchar(256)**|Описывает текущее состояние службы. Ниже приведены возможные значения и соответствующие им описания.<br /><br /> Остановлена Служба остановлена.<br />Другое (ожидание операции запуска): Служба находится в процессе запуска.<br />Другое (ожидание операции завершения): Служба находится в процессе остановки.<br />Установлен Служба выполняется.<br />Другое (ожидается продолжение операций): Служба находится в состоянии ожидания.<br />Другое (ожидание приостановки): Служба находится в процессе приостановки.<br />Приостановлена Служба приостановлена.<br /><br /> Не может иметь значение null.|  
|process_id|**int**|Идентификатор процесса службы. Не может иметь значение null.|  
|last_startup_time|**datetimeoffset(7)**|Дата и время последнего запуска службы. Допускает значение NULL.|  
|service_account|**nvarchar(256)**|Учетная запись, имеющая право управлять этой службой. Данная учетная запись может запускать и останавливать службу или изменять ее свойства. Не может иметь значение null.|  
|filename|**nvarchar(256)**|Полный путь и имя исполняемого файла службы. Не может иметь значение null.|  
|is_clustered|**nvarchar (1)**|Указывает, установлена ли служба в качестве ресурса кластеризованного сервера. Не может иметь значение null.|  
|cluster_nodename|**nvarchar(256)**|Имя узла кластера, на котором установлена служба. Допускает значение NULL.|
|instant_file_initialization_enabled|**nvarchar (1)**|Указывает, включена ли Мгновенная инициализация файлов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для службы.<br /><br />Y = Мгновенная инициализация файлов включена для службы.<br /><br />N = Мгновенная инициализация файлов отключена для службы.<br /><br /> Допускает значение NULL.<br /><br /> **Примечание.** Не применяется к другим службам, таким как агент SQL Server.<br /><br /> **Применимо к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](Начиная с [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]обновления 1 (SP1)).|  

## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также  
 [sys. DM _server_registry &#40;, TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  

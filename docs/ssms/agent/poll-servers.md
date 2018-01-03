---
title: "Опрос серверов | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2dfa83abd424dc53582db0668de594e8177d3beb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="poll-servers"></a>Опрос серверов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] При использовании системы многосерверного администрирования целевые серверы периодически связываются с главным сервером для загрузки на него данных о выполненных заданиях и для получения новых заданий. Процесс взаимодействия с главным сервером называется *опросом сервера* и выполняется через равные *интервалы опроса.*  
  
## <a name="polling-intervals"></a>Интервалы опроса  
Интервал опроса (равный по умолчанию одной минуте) определяет частоту, с которой целевой сервер будет связываться с главным сервером, чтобы загрузить инструкции и передать на него результаты выполнения задания.  
  
Опрашивая главный сервер, целевой сервер считывает назначенные ему операции из таблицы **sysdownloadlist** базы данных **msdb** . Эти операции контролируют многосерверные задания и различные аспекты работы целевого сервера. Примерами таких операций могут служить удаление задания, вставка задания, запуск задания и обновление интервала опроса, заданного на целевом сервере.  
  
Операции можно опубликовать в таблице **sysdownloadlist** двумя способами:  
  
-   явно, вызвав хранимую процедуру **sp_post_msx_operation** ;  
  
-   неявно, используя другие хранимые процедуры задания.  
  
При изменении расписания выполнения многосерверного задания или шагов задания с помощью хранимых процедур задания или при использовании объектов SQL-DMO (SQL Distributed Management Objects) для контроля многосерверных заданий выполните после изменения следующую команду:  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Это обеспечивает синхронизацию целевых серверов с текущим определением задания.  
  
В следующих ситуациях явно публиковать операции не требуется:  
  
-   при использовании среды Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] для контроля многосерверных заданий;  
  
-   при использовании хранимых процедур заданий, не изменяющих расписания выполнения заданий и шагов заданий.  
  
**Принудительный опрос главного сервера целевым сервером**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>См. также:  
[Управление событиями](../../ssms/agent/manage-events.md)  
  

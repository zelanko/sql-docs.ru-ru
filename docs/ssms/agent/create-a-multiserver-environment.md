---
title: "Создание многосерверной среды | Документация Майкрософт"
ms.custom: 
ms.date: 01/30/2017
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
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: "6"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d880677059d8263ae7df35f4c2471e3413f57197
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-a-multiserver-environment"></a>Создание многосерверной среды
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Администрирование нескольких серверов требует настройки главного сервера (MSX) и одного или более целевых серверов (TSX). Задания, которые будут обрабатываться на всех целевых серверах, сначала определяются на главном сервере, а затем загружаются на целевые.  
  
По умолчанию полное шифрование SSL и проверка сертификата включены для соединений между главными и целевыми серверами. Дополнительные сведения см. в статье [Установка параметров шифрования на целевых серверах](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
Если используется большое количество целевых серверов, по возможности не размещайте главный сервер на рабочем сервере, на котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] значительно загружен другими задачами, так как трафик от целевых серверов может снизить производительность рабочего сервера. При переадресации событий на выделенный главный сервер можно централизовать администрирование на одном сервере. Дополнительные сведения см. в статье [Управление событиями](../../ssms/agent/manage-events.md).  
  
> [!NOTE]  
> Чтобы использовать обработку заданий в многосерверном окружении, учетная запись агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] должна быть членом роли базы данных **msdb** **TargetServersRole** на главном сервере. Мастер настройки главного сервера автоматически добавляет к этой роли учетную запись службы в ходе процесса прикрепления  
  
## <a name="considerations-for-multiserver-environments"></a>Замечания по многосерверным средам  
  
При создании многосерверной среды возможны следующие проблемы:  
  
-   Используйте последнюю версию в качестве главного сервера. Поддерживается текущая и две предыдущие версии.

-   Каждый целевой сервер отправляет отчеты только одному главному серверу. Нужно открепить целевой сервер от одного главного сервера перед прикреплением его к другому.  
  
-   Если меняется имя целевого сервера, нужно сначала открепить целевой сервер от главного, а после изменения имени прикрепить снова.  
  
-   Если нужно удалить многосерверную конфигурацию, необходимо отключить все целевые серверы от главного сервера.  
  
-   Службы SQL Server Integration Services поддерживают только серверы, которые имеют такую же или более высокую версию, что и версия главного сервера.  
  
## <a name="related-tasks"></a>Related Tasks  
В следующих разделах описываются типовые задачи при создании многосерверной среды.  
  
|Description|Раздел|  
|---------------|---------|  
|Описывает, как создать главный сервер.|[Создание главного сервера](../../ssms/agent/make-a-master-server.md)|  
|Описывает, как создать целевой сервер.|[Создание целевого сервера](../../ssms/agent/make-a-target-server.md)|  
|Описывает, как прикрепить целевой сервер к главному.|[Прикрепление целевого сервера к главному](../../ssms/agent/enlist-a-target-server-to-a-master-server.md)|  
|Описывает, как исключить целевой сервер из главного.|[Отключение целевого сервера от главного сервера](../../ssms/agent/defect-a-target-server-from-a-master-server.md)|  
|Описывает, как исключить несколько целевых серверов из главного.|[Отключение нескольких целевых серверов от главного](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)|  
|Описывает, как проверить состояние целевого сервера.|[sp_help_targetserver (Transact-SQL)](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)<br /><br />[sp_help_targetservergroup (Transact-SQL)](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)|  
  
## <a name="see-also"></a>См. также:  
[Устранение неполадок, связанных с многосерверными заданиями, использующими учетные записи-посредники](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
  

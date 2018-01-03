---
title: "Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio) | Документация Майкрософт"
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
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b80002e08dd2580f5f36d49f984ab022c430dda6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описано, как задать время, в течение которого агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] будет ожидать завершения выполнения заданий, прежде чем агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] завершит работу в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Установка времени завершения работы задания агента SQL Server**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию члены предопределенной роли сервера **sysadmin** могут задавать время, в течение которого агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] будет ожидать выполнения заданий до того момента, как он завершит работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Настройка завершения выполнения заданий  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо установить интервал выполнения задания.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В разделе **Выбор страницы**выберите пункт **Система заданий**.  
  
4.  Установите **Интервал ожидания при завершении работы** в секундах, чтобы увеличить или уменьшить длительность ожидания завершения работы. Этот параметр определяет, как долго агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] будет ожидать завершения выполняющихся заданий перед завершением работы самого агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  

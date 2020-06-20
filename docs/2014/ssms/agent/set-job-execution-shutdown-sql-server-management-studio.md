---
title: Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1200a7cbd0f6b59e43af81f5414f9946801e093
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067557"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio)
  В этом разделе описывается, как задать время, в течение которого [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент будет ожидать завершения выполнения заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , прежде чем сам агент завершит работу с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Установка времени завершения работы задания агента SQL Server**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 По умолчанию члены предопределенной роли сервера **sysadmin** могут задавать время, в течение которого агент [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет ожидать выполнения заданий до того момента, как завершит работу агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Настройка завершения выполнения заданий  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо установить интервал выполнения задания.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server** и выберите пункт **свойства**.  
  
3.  В разделе **Выбор страницы**выберите пункт **Система заданий**.  
  
4.  Установите **Интервал ожидания при завершении работы** в секундах, чтобы увеличить или уменьшить длительность ожидания завершения работы. Этот параметр определяет, как долго агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет ожидать завершения выполняющихся заданий перед завершением работы самого агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  

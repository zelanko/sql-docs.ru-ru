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
manager: craigg
ms.openlocfilehash: ca9343fe8a6f9e89ba9f26dbbbb12dd7362aff91
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033610"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio)
  В этом разделе описывается, как задать время, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в течение которого агент будет ожидать завершения выполнения заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , прежде чем сам агент завершит [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]работу с помощью.  
  
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
  
  

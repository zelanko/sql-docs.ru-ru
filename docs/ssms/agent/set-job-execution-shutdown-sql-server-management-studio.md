---
title: Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 14e03fffc3a952464bc0949d7023bfa8a20c4f89
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267843"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Настройка интервала ожидания задания при завершении работы (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как задать время, в течение которого агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет ожидать завершения выполнения заданий, прежде чем агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершит работу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Установка времени завершения работы задания агента SQL Server**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию члены предопределенной роли сервера **sysadmin** могут задавать время, в течение которого агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет ожидать выполнения заданий до того момента, как он завершит работу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>Настройка завершения выполнения заданий  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо установить интервал выполнения задания.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В разделе **Выбор страницы**выберите пункт **Система заданий**.  
  
4.  Установите **Интервал ожидания при завершении работы** в секундах, чтобы увеличить или уменьшить длительность ожидания завершения работы. Этот параметр определяет, как долго агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет ожидать завершения выполняющихся заданий перед завершением работы самого агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  

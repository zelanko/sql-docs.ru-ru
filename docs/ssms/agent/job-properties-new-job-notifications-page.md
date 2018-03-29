---
title: Свойства задания — создание задания (страница "Уведомления") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47bbd070ce658140270adb6bbfbd63e71c22fc6c
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="job-properties---new-job-notifications-page"></a>Свойства задания — создание задания (страница "Уведомления")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для установки действий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], выполняемых после завершения задания.  
  
## <a name="options"></a>Параметры  
**Электронная почта**  
Установите этот параметр для отправки электронной почты после завершения задания. Выбрав этот параметр, выберите оператора, которому будет направлено уведомление, и состояние, вызывающее его: **При успешном завершении задания**; **При ошибке задания**или **При завершении задания**.  
  
**Страница**  
Установите этот параметр для отправки электронной почты на пейджер оператора после завершения задания. Выбрав этот параметр, выберите оператора, которому будет направлено уведомление, и состояние, вызывающее его: **При успешном завершении задания**, **При ошибке задания**или **При завершении задания**.  
  
**Команда Net send**  
Выберите этот параметр для использования команды NET SEND для оповещения оператора о завершении задания. Выбрав этот параметр, выберите оператора, которому будет направлено уведомление, и состояние, вызывающее его: **При успешном завершении задания**, **При ошибке задания**или **При завершении задания**.  
  
**Использовать журнал событий приложений Windows**  
Выберите этот параметр для создания записи в журнале событий приложений при завершении выполнения задания. Выбрав этот параметр, выберите состояние, вызывающее запись в журнал: **При успешном завершении задания**, **При ошибке задания**или **При завершении задания**.  
  
**Автоматически удалить задание**  
Выберите этот параметр для автоматического удаления задания после его завершения. Выбрав этот параметр, выберите состояние, которое вызовет удаление задания: **При успешном завершении задания**, **При ошибке задания**или **При завершении задания**.  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
[Практическое руководство. Настройка почты агента SQL Server для использования компонента Database Mail (среда SQL Server Management Studio)](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  

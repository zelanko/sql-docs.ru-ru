---
description: Определение ответов заданий
title: Определение ответов заданий
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 642243221d1f65e8adc05e252c2638f25dfc46d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418010"
---
# <a name="specify-job-responses"></a>Определение ответов заданий
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Ответы заданий определяют действия, выполняемые службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после выполнения задания. Ответы заданий дают гарантию того, что администраторы базы данных будут знать о завершении выполнения заданий и частоте их выполнения. Обычными ответами заданий являются следующие.  
  
-   Уведомление оператора с помощью электронной почты, системы пейджинга или сообщения **net send** .  
  
    Используйте один из этих ответов на задание, если оператор должен выполнить последующие действия. Например, после успешного выполнения задания резервного копирования оператор должен получить напоминание об удалении магнитной ленты с резервной копией и сохранении ее в безопасном месте.  
  
-   Запись сообщений о событиях в журнал приложений Windows.  
  
    Этот ответ можно использовать только для неудачно завершившихся заданий.  
  
-   Автоматическое удаление задания.  
  
    Используйте этот ответ только тогда, когда есть уверенность в том, что не понадобится выполнять это задание повторно.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание|Раздел|  
|-|-|  
|Описывает, как уведомить оператора о состоянии задания.|[Notify an Operator of Job Status](../../ssms/agent/notify-an-operator-of-job-status.md)|  
|Описывает, как записать состояние задания в журнал приложений Windows.|[Write the Job Status to the Windows Application Log](../../ssms/agent/write-the-job-status-to-the-windows-application-log.md)|  
  
## <a name="see-also"></a>См. также:  
[Наблюдение и обработка событий](../../ssms/agent/monitor-and-respond-to-events.md)  
  

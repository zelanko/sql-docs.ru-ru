---
title: Определение ответов заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bc3b747e1dcb1c2d027eb2c1df39c3715c011a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122884"
---
# <a name="specify-job-responses"></a>Определение ответов заданий
  Ответы заданий определяют действия, выполняемые службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после выполнения задания. Ответы заданий дают гарантию того, что администраторы базы данных будут знать о завершении выполнения заданий и частоте их выполнения. Обычными ответами заданий являются следующие.  
  
-   Уведомление оператора с помощью электронной почты, системы пейджинга или сообщения **net send** .  
  
     Используйте один из этих ответов на задание, если оператор должен выполнить последующие действия. Например, после успешного выполнения задания резервного копирования оператор должен получить напоминание об удалении магнитной ленты с резервной копией и сохранении ее в безопасном месте.  
  
-   Запись сообщений о событиях в журнал приложений Windows.  
  
     Этот ответ можно использовать только для неудачно завершившихся заданий.  
  
-   Автоматическое удаление задания.  
  
     Используйте этот ответ только тогда, когда есть уверенность в том, что не понадобится выполнять это задание повторно.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как уведомить оператора о состоянии задания.|[Notify an Operator of Job Status](notify-an-operator-of-job-status.md)|  
|Описывает, как записать состояние задания в журнал приложений Windows.|[Запись данных о состоянии задания в журнал приложений Windows](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>См. также  
 [Наблюдение и обработка событий](monitor-and-respond-to-events.md)  
  
  

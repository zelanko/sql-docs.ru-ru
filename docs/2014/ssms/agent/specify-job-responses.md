---
title: Определение ответов заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d914f36b216bfd49d45e22a259af8df4c781e1b
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809490"
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
|Описывает, как записать состояние задания в журнал приложений Windows.|[Write the Job Status to the Windows Application Log](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>См. также  
 [Наблюдение и обработка событий](monitor-and-respond-to-events.md)  
  
  

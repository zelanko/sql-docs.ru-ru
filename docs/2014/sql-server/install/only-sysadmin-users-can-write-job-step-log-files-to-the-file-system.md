---
title: Только пользователи с правами sysadmin можно написать файлы журнала шагов задания в файловую систему | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e0b7638bbbf33cdd820467cd21edc40a6f5c42ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109622"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Только пользователи с правами sysadmin могут записывать файлы журнала шага задания в файловую систему
  По желанию пользователя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ведет журнал шагов задания.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент может записывать журналы в файловой системе для заданий, которые принадлежат члены **sysadmin** предопределенной роли сервера. Если владелец задания не является членом **sysadmin** роль, и если включена учетная запись-посредник, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент может записывать журналы в файловой системе с использованием учетных данных учетной записи-посредника.  
  
 После обновления все задания, которые принадлежат пользователям, не являющиеся членами из **sysadmin** предопределенной роли сервера лишаются возможности вести журналы в файловой системе. Вместо этого эти пользователи могут выбрать параметр для сохранения своих журналов в таблицу в **msdb** базы данных. Члены **sysadmin** роли по-прежнему могут записывать файлы журнала в файловой системе.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления все задания, которые принадлежат пользователям, не являющиеся членами из **sysadmin** роль будет продолжать работать, но журналы не будут созданы. Для записи журнала шагов задания в таблицу пользователи, не являющиеся членами из **sysadmin** роли необходимо вручную обновить свои задания.  
  
 Дополнительные сведения см. в разделах «Создание заданий», «Создание шагов задания» и «Обработка множественных шагов задания» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
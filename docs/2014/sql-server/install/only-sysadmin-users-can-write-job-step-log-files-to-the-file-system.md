---
title: Только пользователи sysadmin могут записывать файлы журнала шагов задания в файловую систему | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012184"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Только пользователи с правами sysadmin могут записывать файлы журнала шага задания в файловую систему
  По желанию пользователя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ведет журнал шагов задания.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент может записывать журналы в файловую систему для заданий, принадлежащих членам предопределенной роли сервера **sysadmin** . Если владелец задания не является членом роли **sysadmin** , а учетная запись-посредник включена, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент может записывать журналы в файловую систему, используя учетные данные учетной записи-посредника.  
  
 После обновления задания, которые принадлежат пользователям, не являющимся членами предопределенной роли сервера **sysadmin** , больше не могут записывать журналы в файловую систему. Вместо этого эти пользователи могут выбрать параметр для записи журналов в таблицу в базе данных **msdb** . Члены роли **sysadmin** могут по-прежнему записывать файлы журнала в файловую систему.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления задания, которые принадлежат пользователям, не являющимся членами роли **sysadmin** , будут по-прежнему выполняться, но журналы не будут созданы. Для регистрации шагов заданий в таблице пользователи, не являющиеся членами роли **sysadmin** , должны вручную обновить свои задания.  
  
 Дополнительные сведения см. в разделах «Создание заданий», «Создание шагов задания» и «Обработка множественных шагов задания» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  

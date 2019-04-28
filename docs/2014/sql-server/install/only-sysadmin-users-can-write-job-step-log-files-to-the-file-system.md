---
title: Только пользователи с правами sysadmin можно записывать файлы журнала шага задания в файловой системе | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2cb21caf909303fb751d9d616ef67efbac355425
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806032"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Только пользователи с правами sysadmin могут записывать файлы журнала шага задания в файловую систему
  По желанию пользователя [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ведет журнал шагов задания.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент может записывать журналы в файловой системе для заданий, которыми владеют членами **sysadmin** предопределенной роли сервера. Если владелец задания не является членом **sysadmin** роли, и если включена учетная запись-посредник, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент может записывать журналы в файловую систему, используя учетные данные учетной записи-посредника.  
  
 После обновления все задания, которые принадлежат пользователям, которые не являются членами объекта **sysadmin** предопределенной роли сервера лишаются возможности вести журналы в файловой системе. Вместо этого эти пользователи могут выбрать параметр, чтобы записывать туда свои журналы в таблицу в **msdb** базы данных. Членами **sysadmin** роли по-прежнему могут записывать файлы журнала в файловой системе.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления все задания, которые принадлежат пользователям, которые не являются членами объекта **sysadmin** роли продолжится, однако журналы создаваться не будет. Для записи журнала шагов задания в таблицу пользователи, не являющиеся членами из **sysadmin** роли необходимо вручную обновить свои задания.  
  
 Дополнительные сведения см. в разделах «Создание заданий», «Создание шагов задания» и «Обработка множественных шагов задания» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  

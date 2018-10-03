---
title: Удалите вызовы устаревшей команды DBCC CONCURRENCYVIOLATION | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 574b3de41498fa24d2cbd913899d4d071cca6053
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203554"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Удаление вызовов устаревшей команды DBCC CONCURRENCYVIOLATION
  Помощник по обновлению обнаружил использование команды DBCC CONCURRENCYVIOLATION. Эта команда больше не доступна. При выполнении данной команды возвращается ошибка 2526.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Регулятор рабочей нагрузки не входит ни в одну из последних версий выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В связи с этим данная команда была удалена.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите изменения в приложения и скрипты, удалив ссылки на эту устаревшую команду.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  

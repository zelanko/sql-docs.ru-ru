---
title: Удалите вызовы устаревшей команды DBCC CONCURRENCYVIOLATION | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2486546efae7daa63441e12fa350ef878c7daa77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261900"
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
  

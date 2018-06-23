---
title: Удаление вызовов устаревшей команды DBCC CONCURRENCYVIOLATION | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a17b3c844afb6b8b804da258b0330d45dc7208e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187942"
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
  
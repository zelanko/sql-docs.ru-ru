---
title: Недопустимое имя именованного канала может помешать обновлению | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c94c1eeff18bff698e2a6353e29b72dd33278d03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098339"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Неверное имя именованного канала может помешать обновлению
  Обновление завершается ошибкой, если протокол именованных каналов настроен неправильно.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Во время обновления программа установки запускает [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляр с поддержкой общей памяти, именованного канала, поддерживающего только локальные соединения. Если имя канала, указанное на сервере не пусто, оно должно начинаться со строки «\\\\. \pipe\\"недействителен. Если задано недопустимое имя канала, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не запустится и установка завершится ошибкой.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Используйте  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility** укажите допустимое имя канала и снова запустите программу установки.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

---
title: Средство просмотра журналов | Документация Майкрософт
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
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3ff54718ce6ccc39030292041653ebe734594824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190437"
---
# <a name="log-file-viewer"></a>Средство просмотра файлов журнала
  Средство просмотра журнала в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] служит для доступа к сведениям об ошибках и событиях, регистрируемых в файлах журналов.  
  
## <a name="benefits-of-using-log-file-viewer"></a>Преимущества использования средства просмотра журналов  
 Можно просматривать файлы журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальных и удаленных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся вне сети или не могут запуститься. Получить доступ к файлам журналов вне сети можно в списке «Зарегистрированные серверы» или программным способом с помощью запросов WMI и WQL. Дополнительные сведения см. в разделе [Просмотр автономных файлов журнала](view-offline-log-files.md). Ниже приведены типы файлов журналов, которые можно открыть с помощью средства просмотра журналов.  
  
-   Коллекция аудита  
  
-   Сбор данных  
  
-   Database Mail  
  
-   Журнал заданий  
  
-   Планы обслуживания  
  
-   Удаленные планы обслуживания  
  
-   SQL Server  
  
-   SQL Server, агент  
  
-   Windows NT (это события Windows, также доступные из программы просмотра событий Windows)  
  
## <a name="log-file-viewer-tasks"></a>Задачи средства просмотра журналов  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает процедуру открытия средства просмотра журналов в зависимости от того, какие сведения нужно просмотреть.|[открыть средство просмотра журнала](open-log-file-viewer.md)|  
|Описывает процедуру просмотра файлов журналов, находящихся в режиме вне сети, с помощью зарегистрированных серверов, а также процедуру проверки разрешений WMI.|[Просмотр автономных файлов журнала](view-offline-log-files.md)|  
|Предоставляет справку F1 для средства просмотра журналов.|[Справка средства просмотра журнала F1](log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>См. также  
 [Подсистема аудита SQL Server (компонент Database Engine)](../security/auditing/sql-server-audit-database-engine.md)   
 [Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
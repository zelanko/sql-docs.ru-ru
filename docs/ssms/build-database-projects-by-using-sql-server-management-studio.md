---
title: Создание проектов баз данных с использованием среды SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3dda4b94a26b0a2e88d6ad9be75abfa6721cd77
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37983900"
---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a>Создание проектов баз данных с использованием среды SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Проект скрипта базы данных — это организованный набор скриптов, сведений о соединении и шаблонов, связанных с базой данных или одной из частей базы данных. [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] предоставляет [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] для администрирования и проектирования баз данных [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] в контексте проекта скрипта. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] включает конструкторы, редакторы, руководства и мастера, помогающие пользователям в разработке, развертывании и обслуживании баз данных.  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] — это набор административных средств для управления компонентами, относящимися к [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)]. Эта интегрированная среда позволяет пользователям выполнять разнообразные задачи, например резервное копирование данных, редактирование запросов и автоматизацию общих функций в одном интерфейсе.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] включает в себя следующие средства:  
  
-   Редактор кода — богатый возможностями редактор скриптов для написания и редактирования скриптов. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] предоставляет четыре версии редактора кода: редактор запросов [!INCLUDE[ssDE](../includes/ssde_md.md)] для скриптов [!INCLUDE[tsql](../includes/tsql_md.md)] , редактор запросов многомерных выражений, редактор запросов расширения интеллектуального анализа данных и редактор запросов XML/A.  
  
-   Обозреватель объектов для размещения, изменения, создания скрипта или выполнения объектов, принадлежащих экземплярам [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)].  
  
-   Обозреватель шаблонов для размещения и написания сценариев шаблонов.  
  
-   Обозреватель решений для организации и хранения связанных скриптов как части проекта.  
  
-   Окно свойств для отображения текущих свойств выбранных объектов.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] обеспечивает эффективность рабочих процессов, предоставляя:  
  
-   Отключенный доступ. Можно писать и изменять скрипты, не соединяясь с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)].  
  
-   Создание сценариев из любого диалогового окна. Можно создать скрипт из любого диалогового окна, а также читать, изменять, сохранять и многократно использовать скрипты после создания.  
  
-   Немодальные диалоговые окна. При обращении к диалоговому окну интерфейса можно просмотреть другие ресурсы в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] , не закрывая диалоговое окно.  
  
## <a name="solutions-and-script-projects"></a>Решения и проекты скриптов  
Обозреватель решений — это программа для хранения и повторного открытия решений для базы данных. Решения организовывают связанные проекты скрипта и файлы. Проекты скрипта хранят файлы скрипта [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] , шаблоны SQL, сведения о соединении и другие разные файлы. После сохранения скрипта в проекте скриптов у пользователей появляются следующие возможности.  
  
-   Сопровождать управление версиями в скриптах.  
  
-   Хранить параметры результатов со скриптом.  
  
-   Организовывать связанные скрипты в один проект скриптов.  
  
-   Сохранять сведения о соединении со скриптами.  
  
Обозреватель решений — инструмент для разработчиков, создающих и многократно использующих скрипты, связанные с одним и тем же проектом. Если подобная задача потребуется позже, можно использовать группу скриптов, которые были сохранены в проекте. Те, кто уже имеет опыт разработки приложений с помощью среды [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[vsprvs](../includes/vsprvs_md.md)], сориентируются в обозревателе решений довольно легко.  
  
Решение состоит из одного или более проектов скриптов. Проект состоит из одного или более скриптов или соединений. Проект может содержать не только файлы сценариев.  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Создание, анализ и изменение запросов в среде SQL Server Management Studio](http://msdn.microsoft.com/en-us/062051e4-4b77-4969-98ae-d2547c24ce3e)  
[Решения (среда SQL Server Management Studio)](../ssms/solution/solutions-sql-server-management-studio.md)  
  

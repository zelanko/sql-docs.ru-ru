---
title: Решения (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- solutions [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d06a8a05-7201-4055-8cf3-21bcb4e82c25
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2a69fb847726732f3b1321593655f29c3bb2f6d1
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2018
ms.locfileid: "42776363"
---
# <a name="solutions-sql-server-management-studio"></a>Решения (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Решение [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] — это набор из одного или нескольких взаимосвязанных проектов. Проекты — это контейнеры, используемые разработчиками для организации взаимосвязанных файлов (например, для создания наборов широко используемых скриптов администрирования).  
  
## <a name="solution-overview"></a>Общие сведения о решении  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] может использоваться как платформа для разработки скриптов для компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] и служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]. Используйте редакторы кода [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для разработки скриптов и запросов для реляционных и многомерных баз данных, а также для создания наборов взаимосвязанных скриптов и запросов.  
  
Проекты могут включать:  
  
-   Запросы и скрипты для реализации производственных процессов.  
  
-   Сведения о соединении и файлы, используемые запросами и скриптами.  
  
Один или несколько взаимосвязанных проектов могут составлять решение. Управлять решениями и проектами можно с помощью панели обозревателя решений в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
Решения и проекты могут интегрироваться в базы данных Visual SourceSafe (VSS) [!INCLUDE[msCoName](../../includes/msconame_md.md)] или сторонних поставщиков систем управления версиями для отслеживания изменений при разработке и управления жизненным циклом.  
  
## <a name="solution-tasks"></a>Задачи решения  
  
|Описание задачи|Раздел|  
|--------------------|---------|  
|Описывает создание нового решения, которое будет служить контейнером для одного или нескольких проектов.|[Создание нового решения](../../ssms/solution/create-a-new-solution.md)|  
|Описывает добавления существующего решения в обозреватель решений.|[Открытие существующего решения](../../ssms/solution/open-an-existing-solution.md)|  
|Описывает закрытие решения.|[Закрытие решения](../../ssms/solution/close-a-solution.md)|  
|Описывает удаление решения.|[Удаление решения](../../ssms/solution/delete-a-solution.md)|  
|Описывает копирование элементов между проектами.|[Копирование элементов в решении](../../ssms/solution/copy-items-in-a-solution.md)|  
|Описывает удаление элементов проекта или всего проекта.|[Перемещение или удаление элемента или проекта](../../ssms/solution/remove-or-delete-an-item-or-project.md)|  
|Описывает перемещение элементов между проектами в решении.|[Перемещение элементов в решении](../../ssms/solution/move-items-in-a-solution.md)|  
|Описывает переименование решения или элементов в решении.|[Переименование элементов решений и проектов](../../ssms/solution/rename-solutions-and-project-items.md)|  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Проекты (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)  
[Обозреватель решений системы управления версиями](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  

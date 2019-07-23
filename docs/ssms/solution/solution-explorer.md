---
title: Обозреватель решений | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e0f392462b9bd3adf05f5cbbb528daf838fa7aa3
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264753"
---
# <a name="solution-explorer"></a>Обозреватель решений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Панель обозревателя решений в среде [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит контейнеры (проекты) для управления такими элементами, как скрипты базы данных, запросы, подключения к данным и файлы. Один или несколько связанных между собой проектов могут быть объединены в контейнер, который называется решением.  
  
Решение содержит один или несколько проектов, а также файлы и метаданные, которые позволяют определить решение как единое целое. Проект — это набор файлов и относящихся к ним метаданных, например сведений о соединении. Решения и проекты содержат элементы, которые представляют собой скрипты, запросы, сведения о соединениях и файлы, необходимые для создания решения базы данных.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a>Преимущества использования решений  
Эти контейнеры позволяют:  
  
-   реализовать систему управление версиями для запросов и скриптов;  
  
-   управлять параметрами как решения в целом, так и конкретных проектов;  
  
-   облегчить работу с файлами и позволить сосредоточиться на работе с элементами, которые составляют решение базы данных;  
  
-   добавлять элементы одновременно к нескольким проектам решения либо ко всему решению, не указывая элемент в каждом из проектов;  
  
-   работать с различными файлами, формат которых не зависит от решений и проектов.  
  
Элементы, содержащиеся в проектах, зависят от типа проекта и от того, используется ли среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="related-tasks"></a>Связанные задачи  
Используйте следующие разделы для начала работы с решениями SQL Server.  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как добавить один или несколько проектов в решение.|[Решения (среда SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)|  
|Описывает, как создать проект и добавить элементы, например скрипты и соединения.|[Проекты (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)|  
|Сведения о файлах, используемых средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для управления решениями и файлами.|[Файлы для управления решениями и проектами](../../ssms/solution/files-that-manage-solutions-and-projects.md)|  
  

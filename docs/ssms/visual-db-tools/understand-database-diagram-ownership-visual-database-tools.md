---
title: "Основные сведения о владении диаграммами баз данных (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 685a25b7968b24e729f53a943276d8cdaad33b7f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Основные сведения о владении диаграммами баз данных (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Чтобы использовать конструктор схем баз данных, член роли db_owner (роль баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]) должен выполнить его настройку для обеспечения управления доступом к диаграммам. Каждая диаграмма имеет одного и только одного владельца — пользователя, который ее создал. Дополнительные сведения о настройке построения диаграмм см. в разделе [Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
Некоторые сведения о принадлежности диаграмм, которые нужно учитывать:  
  
-   Хотя создать диаграмму может любой пользователь базы данных, просмотреть диаграмму после создания могут только ее создатель и члены роли db_owner.  
  
-   Право владельца диаграммы можно передать только членам роли db_owner. Это возможно, только если предыдущий владелец диаграммы был удален из базы данных.  
  
-   Если владелец диаграммы был удален из базы данных, диаграмма остается в базе данных, пока член роли db_owner не попытается ее открыть. В этот момент член роли db_owner может получить права владельца диаграммы.  
  
## <a name="see-also"></a>См. также:  
[Работа с диаграммами баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  

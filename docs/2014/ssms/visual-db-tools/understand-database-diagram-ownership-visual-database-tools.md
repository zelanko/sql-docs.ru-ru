---
title: Основные сведения о владении диаграммами баз данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6a05d1be7a194bd3ed47aed4936cdc51d479e81f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194633"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Основные сведения о владении диаграммами баз данных (визуальные инструменты для баз данных)
  Чтобы использовать конструктор схем баз данных, член роли db_owner (роль баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) должен выполнить его настройку для обеспечения управления доступом к диаграммам. Каждая диаграмма имеет одного и только одного владельца — пользователя, который ее создал. Дополнительные сведения о настройке схем см [задайте копии базы данных конструктор схем &#40;визуальные инструменты для баз данных&#41;](visual-database-tools.md).  
  
 Некоторые сведения о принадлежности диаграмм, которые нужно учитывать:  
  
-   Хотя создать диаграмму может любой пользователь базы данных, просмотреть диаграмму после создания могут только ее создатель и члены роли db_owner.  
  
-   Право владельца диаграммы можно передать только членам роли db_owner. Это возможно, только если предыдущий владелец диаграммы был удален из базы данных.  
  
-   Если владелец диаграммы был удален из базы данных, диаграмма остается в базе данных, пока член роли db_owner не попытается ее открыть. В этот момент член роли db_owner может получить права владельца диаграммы.  
  
## <a name="see-also"></a>См. также  
 [Работа с диаграммами базы данных &#40;визуальные средства базы данных&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных)](visual-database-tools.md)  
  
  
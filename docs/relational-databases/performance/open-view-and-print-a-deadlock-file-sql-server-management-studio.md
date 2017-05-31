---
title: "Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9c77238f4fe5aa1c9078acd9d4a691c4242f4ce9
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio)
  Когда [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] создает взаимоблокировку, можно собрать и сохранить в файле сведения о взаимоблокировке. После того как файл взаимоблокировок был сохранен, его можно открыть в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы просмотреть или распечатать.  
  
### <a name="to-open-and-view-a-deadlock-file"></a>Открытие и просмотр файла взаимоблокировок  
  
1.  В меню **Файл** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]укажите **Открыть**, затем выберите пункт **Файл**.  
  
2.  В диалоговом окне **Открытие файла** выберите тип файлов XDL в списке **Файлы типа** . Теперь отфильтрованный список содержит только файлы взаимоблокировок.  
  
### <a name="to-print-a-deadlock-file"></a>Распечатка файла взаимоблокировок  
  
1.  В меню **Файл** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]укажите **Открыть** , затем выберите пункт **Файл**.  
  
2.  В диалоговом окне **Открытие файла** выберите тип файлов XDL в списке **Файлы типа** . Теперь отфильтрованный список содержит только файлы взаимоблокировок.  
  
3.  Выберите файл взаимоблокировок, который необходимо распечатать, и нажмите кнопку **Открыть**.  
  
4.  В меню **Файл** выберите **Печать.**  
  
## <a name="see-also"></a>См. также:  
 [Сохранение графов взаимоблокировок (приложение SQL Server Profiler)](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  

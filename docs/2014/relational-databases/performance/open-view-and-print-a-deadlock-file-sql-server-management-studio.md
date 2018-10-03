---
title: Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4a45daf3d20da1b431ce31ef5d6756ee17ce264f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155494"
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
  
## <a name="see-also"></a>См. также  
 [Сохранение графов взаимоблокировок (приложение SQL Server Profiler)](save-deadlock-graphs-sql-server-profiler.md)  
  
  

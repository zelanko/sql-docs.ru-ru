---
title: Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 394a06c9d5e60f94308f2b63508e089a2082c266
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311664"
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
  
  

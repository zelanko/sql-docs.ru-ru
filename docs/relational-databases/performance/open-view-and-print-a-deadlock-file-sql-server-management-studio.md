---
title: Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: performance
ms.reviewer: ''
ms.suite: sql
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
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 971e5ae6448c26cea0c7212fac45bad5ff26e08f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>Открытие, просмотр и печать файла взаимоблокировок (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Когда [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] создает взаимоблокировку, можно собрать и сохранить в файле сведения о взаимоблокировке. После того как файл взаимоблокировок был сохранен, его можно открыть в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], чтобы просмотреть или напечатать.  
  
## <a name="open-and-view-a-deadlock-file"></a>Открытие и просмотр файла взаимоблокировок  
  
1. В меню **Файл** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] наведите указатель на пункт **Открыть**, а затем выберите пункт **Файл**.  
  
2. В диалоговом окне **Открытие файла** выберите тип файлов XDL в списке **Файлы типа** . Теперь отфильтрованный список содержит только файлы взаимоблокировок.  
  
## <a name="print-a-deadlock-file"></a>Печать файла взаимоблокировок  
  
1. В меню **Файл** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] наведите указатель на пункт **Открыть**, а затем выберите пункт **Файл**.  
  
2. В диалоговом окне **Открытие файла** выберите тип файлов XDL в списке **Файлы типа** . Теперь отфильтрованный список содержит только файлы взаимоблокировок.  
  
3. Выберите файл взаимоблокировок, который необходимо напечатать, и нажмите кнопку **Открыть**.  
  
4. В меню **Файл** выберите пункт **Печать**.  
  
## <a name="see-also"></a>См. также раздел  
 [Сохранение графов взаимоблокировок (приложение SQL Server Profiler)](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  

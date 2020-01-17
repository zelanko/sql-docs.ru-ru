---
title: Открытие, просмотр и печать файла взаимоблокировок (SSMS)
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c305d9fd08ffcdd1c4b66d90d834c8f0fb6dead5
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165764"
---
# <a name="open-view-and-print-a-deadlock-file-in-sql-server-management-studio-ssms"></a>Открытие, просмотр и печать файла взаимоблокировок в среде SQL Server Management Studio (SSMS)

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
  
  

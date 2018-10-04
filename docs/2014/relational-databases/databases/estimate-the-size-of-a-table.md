---
title: Оценка размера таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 60d9214fff9ef50ebcaf506006a68ad486d2edbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094084"
---
# <a name="estimate-the-size-of-a-table"></a>Оценка размера таблицы
  Оценить пространство, необходимое для хранения данных в таблице, можно с помощью следующих шагов:  
  
1.  Рассчитайте пространство, необходимое для кучи или кластеризованного индекса, с помощью инструкций в статьях [Оценка размера кучи](estimate-the-size-of-a-heap.md) и [Оценка размера кластеризованного индекса](estimate-the-size-of-a-clustered-index.md).  
  
2.  Вычислите необходимое пространство для каждого некластеризованного индекса с помощью инструкций в статье [Оценка размера некластеризованного индекса](estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Сложите значения, рассчитанные на шаге 1 и 2.  
  
## <a name="see-also"></a>См. также  
 [Оценка размера базы данных](estimate-the-size-of-a-database.md)   
 [Оценка размера кучи](estimate-the-size-of-a-heap.md)   
 [Оценка размера кластеризованного индекса](estimate-the-size-of-a-clustered-index.md)   
 [Оценка размера некластеризованного индекса](estimate-the-size-of-a-nonclustered-index.md)  
  
  

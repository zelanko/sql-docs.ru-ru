---
title: Оценка размера таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2e36482008cdbd32cfd11c1c8f49f330ee606f77
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="estimate-the-size-of-a-table"></a>Оценка размера таблицы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Оценить пространство, необходимое для хранения данных в таблице, можно с помощью следующих шагов:  
  
1.  Рассчитайте пространство, необходимое для кучи или кластеризованного индекса, с помощью инструкций в статьях [Оценка размера кучи](../../relational-databases/databases/estimate-the-size-of-a-heap.md) и [Оценка размера кластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Вычислите необходимое пространство для каждого некластеризованного индекса с помощью инструкций в статье [Оценка размера некластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Сложите значения, рассчитанные на шаге 1 и 2.  
  
## <a name="see-also"></a>См. также:  
 [Оценка размера базы данных](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Оценка размера кучи](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Оценка размера кластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Оценка размера некластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  

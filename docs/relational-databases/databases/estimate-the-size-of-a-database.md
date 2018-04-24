---
title: Оценка размера базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 180e6a5d6c74a8a2859c6f30566f113d3c14f771
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="estimate-the-size-of-a-database"></a>Оценка размера базы данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  При проектировании базы данных иногда требуется оценить, каким будет размер базы данных после заполнения ее данными. Оценка размера базы данных помогает определить конфигурацию аппаратного обеспечения, необходимую для достижения следующих целей:  
  
-   Получения производительности, необходимой для работы приложений.  
  
-   Обеспечения соответствующего физического объема места на диске, необходимого для хранения данных и индексов.  
  
 Оценка размера базы данных помогает определить, требуется ли доработка проекта базы данных. Например, может оказаться, что предполагаемый размер базы данных слишком велик для предприятия, а потому требуется ее нормализация. Напротив, оценочный размер может оказаться меньше, чем ожидалось. Это позволит денормализовать базу данных для повышения производительности запросов.  
  
 При оценке размера базы данных производится оценка размера каждой из таблиц и сложение полученных значений. Размер таблицы зависит от наличия у этой таблицы индексов и, если они есть, от их типов.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Оценка размера таблицы](../../relational-databases/databases/estimate-the-size-of-a-table.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в таблице и связанных индексах.|  
|[Оценка размера кучи](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в куче. Кучей называется таблица, не имеющая кластеризованного индекса.|  
|[Оценка размера кластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|Определяет шаги и вычисления, необходимые для оценки места на диске, необходимого для хранения данных в кластеризованном индексе.|  
|[Оценка размера некластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в некластеризованном индексе.|  
  
  

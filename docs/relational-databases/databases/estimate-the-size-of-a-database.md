---
title: Оценка размера базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86494a697cb16e0e47d7d52de0312b3a799f68b4
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51557811"
---
# <a name="estimate-the-size-of-a-database"></a>Оценка размера базы данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  При проектировании базы данных иногда требуется оценить, каким будет размер базы данных после заполнения ее данными. Оценка размера базы данных помогает определить конфигурацию аппаратного обеспечения, необходимую для достижения следующих целей:  
  
-   Получения производительности, необходимой для работы приложений.  
  
-   Обеспечения соответствующего физического объема места на диске, необходимого для хранения данных и индексов.  
  
 Оценка размера базы данных помогает определить, требуется ли доработка проекта базы данных. Например, может оказаться, что предполагаемый размер базы данных слишком велик для предприятия, а потому требуется ее нормализация. Напротив, оценочный размер может оказаться меньше, чем ожидалось. Это позволит денормализовать базу данных для повышения производительности запросов.  
  
 При оценке размера базы данных производится оценка размера каждой из таблиц и сложение полученных значений. Размер таблицы зависит от наличия у этой таблицы индексов и, если они есть, от их типов.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Оценка размера таблицы](../../relational-databases/databases/estimate-the-size-of-a-table.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в таблице и связанных индексах.|  
|[Оценка размера кучи](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в куче. Кучей называется таблица, не имеющая кластеризованного индекса.|  
|[Оценка размера кластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|Определяет шаги и вычисления, необходимые для оценки места на диске, необходимого для хранения данных в кластеризованном индексе.|  
|[Оценка размера некластеризованного индекса](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|Определяет шаги и вычисления для оценки места на диске, необходимого для хранения данных в некластеризованном индексе.|  
  
  

---
title: Настройка подключения Polybase
description: В этой статье объясняется, как настроить Polybase в параллельном хранилище данных для подключения к внешним источникам данных хранилища больших двоичных объектов Hadoop или Microsoft Azure. Используйте Polybase для выполнения запросов, которые объединяют данные из нескольких источников, включая Hadoop, хранилище BLOB-объектов Azure и Параллельное хранилище данных.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 352f51e0d53c9dc145b1faf1832faf59587fef6f
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243095"
---
# <a name="configure-polybase-connectivity"></a>Настройка подключения Polybase
Polybase позволяет системе аналитики (ТД) обрабатывать запросы Transact-SQL, которые могут считывать данные из внешних источников данных и записывать их в них. Те же запросы, которые обращаются к внешним данным, могут также включать таблицы связей в ТД. Это позволяет объединять данные из внешних источников с высокоценными реляционными данными в базах данных APS.

![Логика PolyBase](media/polybase/polybase-logical.png)

Polybase на ТД поддерживает чтение и запись в файловую систему Hadoop (HDFS) и хранилище BLOB-объектов Azure. Polybase также может отправлять некоторые вычисления в узлы Hadoop в виде заданий MapReduce для оптимизации общей производительности запросов. Polybase на ТД может использоваться с файлами с разделителями (Text, ORC и Parquet). Полное описание и его возможности см. в разделе [что такое polybase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) .

> [!NOTE]
> В настоящее время APS поддерживает только стандартное локально избыточное хранилище BLOB-объектов (LRS) общего назначения версии 1.

## <a name="features-and-limitations"></a>Возможности и ограничения
Ознакомьтесь с [возможностями и ограничением](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-versioned-feature-summary) для получения сводки о доступных функциях polybase и известных ограничениях для ТД и других SQL Server продуктов.

> [!NOTE] 
> Остальные статьи, связанные с Polybase, описывают способы, как настроить Polybase на ТД 2016 (AU6) и более поздних версий.

## <a name="see-also"></a>См. также
- [Hadoop](polybase-configure-hadoop.md)
- [Хранилище BLOB-объектов Azure](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  

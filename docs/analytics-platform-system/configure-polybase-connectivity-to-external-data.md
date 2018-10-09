---
title: Настройка подключения PolyBase - Analytics Platform System | Документация Майкрософт
description: В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Microsoft Azure или Hadoop хранилища BLOB-объектов источников данных. Для выполнения запросов, объединяющие данные из нескольких источников, включая Hadoop, хранилища BLOB-объектов Azure и Parallel Data Warehouse с помощью PolyBase.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: da6d71521f72ff23b4caf2f27dbc663dee684592
ms.sourcegitcommit: 5afec8b4b73ce1727e4e5cf875d1e1ce9df50eab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2018
ms.locfileid: "47450299"
---
# <a name="what-is-polybase"></a>Что такое PolyBase?
PolyBase позволяет вашей Analytics Platform System (APS) для обработки запросов Transact-SQL, которые могут считывать данные из и записывать данные с внешними источниками данных. Те же запросы, которые обращаются к внешним данным можно также включить связанных таблиц в вашей ТД. Это позволяет объединять данные из внешних источников с реляционными данными в базах данных APS, высокой ценности.

![Логическая схема использования PolyBase](media/polybase/polybase-logical.png)

PolyBase на точках доступа поддерживает чтение и запись в файловой системе Hadoop (HDFS) и хранилище BLOB-объектов. PolyBase также имеет возможность Включение некоторых вычислений в Hadoop узлы как задания mapreduce, чтобы оптимизировать производительность запросов. PolyBase на точках доступа могут работать с разделителями, ORC и Parquet файлы. См. в разделе [что такое PolyBase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) для полного описания и ее возможностях.

> [!NOTE]
> APS в настоящее время поддерживает только стандартные общего назначения версии 1 локально избыточное (LRS) хранилища больших двоичных объектов.

## <a name="features-and-limitations"></a>Возможности и ограничения
См. в разделе [возможности и ограничения на](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-versioned-feature-summary) сводку PolyBase функций и известных ограничений на APS и других продуктов SQL Server.

> [!NOTE] 
> Остальная часть PolyBase связанные статьи описывают способы настройки PolyBase, APS 2016 г. (AU6) и более поздних версий.

## <a name="see-also"></a>См. также
- [Hadoop](polybase-configure-hadoop.md)
- [Хранилище больших двоичных объектов](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  

---
title: "Документация по ширине World Importers | Документы Microsoft"
ms.prod: world-wide-importers
ms.prod_service: sql-non-specified
ms.service: samples
ms.component: 
ms.technology: samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17cabd9d-cb2f-436c-ad9c-ce02225808b7
caps.latest.revision: "3"
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 367581f176b148fe65f8fee44bfdbb7a6eb5e8ec
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="wide-world-importers-documentation"></a>Расширенный World Importers документации
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Компания Wide World Importers — новый образец базы данных SQL Server 2016 и база данных SQL Azure. Он иллюстрирует основные возможности SQL Server 2016 и база данных SQL Azure для обработки транзакций (OLTP), хранения данных и аналитики (OLAP), а также транзакции гибридных и аналитических рабочих нагрузок обработки (HTAP).

## <a name="about-this-sample"></a>Об этом образце

Wide World Importers — образец комплексное базы данных, и иллюстрирует структуры базы данных и показано, как можно использовать функции SQL Server в приложении.

Обратите внимание, что образец должен представлять обычной базой данных. Он не включает все возможности SQL Server. Схема базы данных соответствует один общий набор стандартов, но существует множество способов, которые один может создать базу данных.

**Последний выпуск**: [wide world-importers выпуска](http://go.microsoft.com/fwlink/?LinkID=800630)

**Исходный код образца**: [wide world-importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers).

**Отзыв**: Отправьте для [ sqlserversamples@microsoft.com ](mailto:sqlserversamples@microsoft.com).

Документация в этом образце организована следующим образом:

## <a name="overview"></a>Обзор

Общие сведения о примере компания Wide World Importers и рабочие процессы, описанной в этом образце.

## <a name="main-oltp-database-wideworldimporters"></a>OLTP главной базы данных WideWorldImporters

Инструкции для установки и настройки ядра базы данных WideWorldImporters, используемый для обработки транзакций (OLTP - оперативной обработки транзакций) и оперативной аналитики (HTAP - обработка транзакций и Analytical гибридного).

Описание схемы и таблицы, используемые в базе данных WideWorldImporters.  

Описывает, каким образом WideWorldImporters использует функции SQL Server core.

Примеры запросов для базы данных WideWorldImporters.

## <a name="data-warehousing-and-analytics-database-wideworldimportersdw"></a>Хранение данных и аналитики WideWorldImportersDW базы данных

Инструкции для установки и настройки OLAP базы данных WideWorldImportersDW.

Описание схемы и таблицы, используемые в базе данных WideWorldImportersDW, которая является образец базы данных для хранения данных и аналитики обработки (OLAP).

Рабочий процесс для процесса ETL (Extract, Transform, Load), который перемещает данные из WideWorldImporters транзакций базы данных в хранилище данных WideWorldImportersDW.

Описывает, каким образом WideWorldImportersDW использует функции SQL Server для аналитической обработки.

Примеры запросов аналитики, использование WideWorldImportersDW базы данных.

## <a name="data-generation"></a>Создание данных

Описывает, как дополнительные данные могут быть созданы в образце базы данных, например Вставка продажи и покупки данных до текущей даты.

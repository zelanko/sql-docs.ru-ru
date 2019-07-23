---
title: Выполняющаяся в памяти база данных | Документация Майкрософт
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- in-memory database
- feature, in-memory database
- in-memory
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: d61ea85f5c1d7784faaf1d094e2fa858bffcd8c2
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68255414"
---
# <a name="in-memory-database"></a>Выполняющаяся в памяти база данных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Выполняющаяся в памяти база данных — это обобщающий термин для функций в SQL Server, использующих технологии выполнения в памяти. По мере появления новых функций на основе выполнения в памяти эта страница будет обновляться.

## <a name="hybrid-buffer-pool"></a>Гибридный буферный пул

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md) предоставляет ядру СУБД прямой доступ к страницам данных в файлах базы данных, хранимых на устройствах с постоянной памятью (PMEM).

## <a name="memory-optimized-tempdb-metadata"></a>Оптимизированные для памяти метаданные TempDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] появилась новая функция — [оптимизированные для памяти метаданные tempdb](./databases/tempdb-database.md#memory-optimized-tempdb-metadata), которая эффективно устраняет некоторые узкие места состязаний и открывает новый уровень масштабируемости для рабочих нагрузок, активно использующих tempdb.

## <a name="in-memory-oltp"></a>Выполняющаяся в памяти OLTP

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Выполняющаяся в памяти OLTP](./in-memory-oltp/in-memory-oltp-in-memory-optimization.md) — первоклассная технология, доступная в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../includes/sssds-md.md)] и предназначенная для оптимизации производительности обработки транзакций, приема и загрузки данных, а также сценариев с временными данными.

**Применимо к:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="persistent-memory-support-for-linux"></a>Поддержка постоянной памяти для Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] добавляет поддержку устройств с постоянной памятью (PMEM) для Linux, предоставляя полноценный компонент паравиртуализации для файлов данных и журналов транзакций, размещенных в [постоянной памяти](../linux/sql-server-linux-configure-pmem.md).

**Применимо к:** [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

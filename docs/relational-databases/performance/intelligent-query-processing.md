---
title: Интеллектуальная обработка запросов в базах данных Microsoft SQL | Документы Майкрософт
description: Функции интеллектуальной обработки запросов для повышения производительности запросов в SQL Server и базе данных SQL Azure.
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7786fd048f1698c90f379450b31e0bac3457706e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455774"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Интеллектуальная обработка запросов в базах данных SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Семейство функций **интеллектуальной обработки запросов** содержит функции, которые оказывают широкое влияние на производительность существующих рабочих нагрузок и требуют минимальных усилий при реализации.   К таким функциям относятся улучшения существующих конструкций, а также внедрение адаптивных методов и возможностей.  

## <a name="adaptive-query-processing"></a>Адаптивная обработка запросов
Семейство функций интеллектуальной обработки запросов включает семейство функций адаптивной обработки запросов, которое впервые появилось в SQL Server 2017 и базе данных SQL Azure. В этом семействе были реализованы совершенно новые возможности обработки, которые адаптируют стратегии оптимизации к условиям среды выполнения рабочей нагрузки вашего приложения:
- **Адаптивные соединения в пакетном режиме**. Эта функция позволяет динамически переключить ваш план на лучшую стратегию соединения во время выполнения с использованием одного кэшированного плана.
- **Обратная связь по временно предоставляемому буферу памяти в пакетном режиме**. Эта функция пересчитывает фактический объем памяти, необходимый для выполнения запроса, и обновляет размер временно предоставляемого буфера памяти для кэшированного плана. Это позволяет сократить избыточное использование временно предоставляемых буферов памяти и решить проблему с недостатком временно предоставляемых буферов памяти, который вызывает избыточную запись на диск.
- **Выполнение с чередованием для функций с табличным значением с несколькими инструкциями**. При выполнении с чередованием мы используем фактическое количество строк из функции для принятия обоснованного решения в отношении плана запроса. 

Дополнительные сведения об адаптивной обработке запросов см. в разделе [Адаптивная обработка запросов в базах данных SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="see-also"></a>См. также раздел
[Центр производительности для базы данных SQL Azure и ядра СУБД SQL Server](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md)    
[Справочник по логическим и физическим операторам Showplan](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Соединения](../../relational-databases/performance/joins.md)    
[Демонстрация адаптивной обработки запросов](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        

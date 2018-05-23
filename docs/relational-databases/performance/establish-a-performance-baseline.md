---
title: Определение базовых показателей производительности | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0a9e8fd61f47752c5ad3a730dcb41393e370d168
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="establish-a-performance-baseline"></a>Формирование базовых показателей производительности
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Чтобы определить, оптимально ли функционирует система [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо измерять производительность через определенные промежутки времени, даже если не возникает никаких проблем, для установления базового уровня производительности. Сравните каждый новый набор измерений с полученными ранее.  
  
 Ниже представлены зоны, влияющие на производительность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   ресурсы системы (оборудование);  
  
-   архитектура сети;  
  
-   операционная система;  
  
-   приложения базы данных;  
  
-   клиентские приложения.  
  
 Как минимум используйте измерения базового уровня для определения следующих значений:  
  
-   пиковые и непиковые часы операции;  
  
-   время ответа на подачу запроса или команды пакета;  
  
-   время завершения резервного копирования и восстановления базы данных.  
  
 После установления базового уровня производительности сервера сравните статистику базовых строк с текущей производительностью сервера. Числа намного выше и намного ниже базового уровня являются кандидатами для дальнейшего изучения. Они могут указывать зоны, которым необходимы настройка или повторная конфигурация. Например, если количество времени для выполнения набора запросов увеличивается, изучите запросы, чтобы определить, могут ли они быть переписаны и есть ли необходимость добавлять статистику столбца или новые индексы.  
  
## <a name="see-also"></a>См. также:  
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

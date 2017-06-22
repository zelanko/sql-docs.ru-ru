---
title: "Определение базовых показателей производительности | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6d1c546387df6352a1eb59b0c0310d86a630a342
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="establish-a-performance-baseline"></a>Формирование базовых показателей производительности
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
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

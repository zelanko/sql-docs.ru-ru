---
title: "Задание значения параметра базы данных AUTO_SHRINK, равного OFF | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Лучшие решения [компонент Database Engine]"
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Задание значения параметра базы данных AUTO_SHRINK, равного OFF
  Это правило проверяет, имеет ли параметр базы данных AUTO_SHRINK значение OFF. Нередко сжатие и расширение базы данных ведет к физической фрагментации.  
  
## Рекомендации  
 Присвойте параметру базы данных AUTO_SHRINK значение OFF. Если известно, что освобождаемое место не понадобится в будущем, можно освободить это место, выполнив сжатие базы данных вручную.  
  
## Дополнительные сведения см. в разделе  
 Статья [315512](http://go.microsoft.com/fwlink/?linkid=117750)базы знаний Майкрософт  
  
## См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
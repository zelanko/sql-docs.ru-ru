---
title: Упреждающее кэширование (измерения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6f5e6bab81e982adbf8ee443bd84a5e806b960db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727302"
---
# <a name="proactive-caching-dimensions"></a>Упреждающее кэширование (измерения)
  Упреждающее кэширование позволяет автоматически создавать кэш MOLAP для объектов OLAP, а также управлять им. Кубы мгновенно реагируют на изменения, которые происходят с данными из базы данных, благодаря уведомлениям, получаемым от базы данных. Цель упреждающего кэширования — совмещение производительности, характерной для традиционного MOLAP, со скоростью и простотой управления ROLAP.  
  
 Простой объект <xref:Microsoft.AnalysisServices.ProactiveCaching> содержит спецификации времени и уведомления таблиц. Спецификация времени определяет временной промежуток, за который кэш обновляется после получения уведомления об изменении. В уведомлении таблиц определяется схема обмена уведомлениями между таблицей данных и объектом <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  

---
title: Упреждающее кэширование (измерения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9849f5ce2f82b44772a1faf360a530eb712c6dbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224574"
---
# <a name="proactive-caching-dimensions"></a>Упреждающее кэширование (измерения)
  Упреждающее кэширование позволяет автоматически создавать кэш MOLAP для объектов OLAP, а также управлять им. Кубы мгновенно реагируют на изменения, которые происходят с данными из базы данных, благодаря уведомлениям, получаемым от базы данных. Цель упреждающего кэширования — совмещение производительности, характерной для традиционного MOLAP, со скоростью и простотой управления ROLAP.  
  
 Простой объект <xref:Microsoft.AnalysisServices.ProactiveCaching> содержит спецификации времени и уведомления таблиц. Спецификация времени определяет временной промежуток, за который кэш обновляется после получения уведомления об изменении. В уведомлении таблиц определяется схема обмена уведомлениями между таблицей данных и объектом <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  

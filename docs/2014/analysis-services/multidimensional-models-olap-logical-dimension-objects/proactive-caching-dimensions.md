---
title: Упреждающее кэширование (измерения) | Документы Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 86634be8be55ff48f2eac1a4c4453f7cdd5eddb9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190860"
---
# <a name="proactive-caching-dimensions"></a>Упреждающее кэширование (измерения)
  Упреждающее кэширование позволяет автоматически создавать кэш MOLAP для объектов OLAP, а также управлять им. Кубы мгновенно реагируют на изменения, которые происходят с данными из базы данных, благодаря уведомлениям, получаемым от базы данных. Цель упреждающего кэширования — совмещение производительности, характерной для традиционного MOLAP, со скоростью и простотой управления ROLAP.  
  
 Простой объект <xref:Microsoft.AnalysisServices.ProactiveCaching> содержит спецификации времени и уведомления таблиц. Спецификация времени определяет временной промежуток, за который кэш обновляется после получения уведомления об изменении. В уведомлении таблиц определяется схема обмена уведомлениями между таблицей данных и объектом <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
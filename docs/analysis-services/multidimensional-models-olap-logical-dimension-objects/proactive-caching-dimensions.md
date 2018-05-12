---
title: Упреждающее кэширование (измерения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db9b77c799f674b39f3c6a66a6812464896abefc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="proactive-caching-dimensions"></a>Упреждающее кэширование (измерения)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Упреждающее кэширование позволяет автоматически создавать кэш MOLAP для объектов OLAP, а также управлять им. Кубы мгновенно реагируют на изменения, которые происходят с данными из базы данных, благодаря уведомлениям, получаемым от базы данных. Цель упреждающего кэширования — совмещение производительности, характерной для традиционного MOLAP, со скоростью и простотой управления ROLAP.  
  
 Простой объект <xref:Microsoft.AnalysisServices.ProactiveCaching> содержит спецификации времени и уведомления таблиц. Спецификация времени определяет временной промежуток, за который кэш обновляется после получения уведомления об изменении. В уведомлении таблиц определяется схема обмена уведомлениями между таблицей данных и объектом <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  

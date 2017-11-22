---
title: "Определение связей фактов и свойств связей фактов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46cf5d6b942751fb0ca76942e8762cec271a5b4c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Определение связей фактов и свойств связей фактов
  При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли связь измерений фактов, и задать для параметра использования измерения значение **Fact**. Связь измерений фактов можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов. Связь фактов между измерением и группой мер имеет следующие ограничения.  
  
-   Измерение куба может иметь только одну связь фактов с конкретной группой мер.  
  
-   Измерение куба может иметь отдельные связи фактов с несколькими группами мер.  
  
-   Атрибут гранулярности для связи должен быть ключевым атрибутом (таким как номер транзакции) для измерения. Это создает связь «один к одному» между измерением и фактами в таблице фактов.  
  
  

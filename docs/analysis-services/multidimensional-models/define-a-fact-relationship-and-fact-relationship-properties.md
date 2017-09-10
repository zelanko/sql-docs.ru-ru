---
title: "Определение связей фактов и свойств связей фактов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0b86ebd4da388cbaf303bcdab92fe3fce3994fe1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Определение связей фактов и свойств связей фактов
  При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли связь измерений фактов, и задать для параметра использования измерения значение **Fact**. Связь измерений фактов можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов. Связь фактов между измерением и группой мер имеет следующие ограничения.  
  
-   Измерение куба может иметь только одну связь фактов с конкретной группой мер.  
  
-   Измерение куба может иметь отдельные связи фактов с несколькими группами мер.  
  
-   Атрибут гранулярности для связи должен быть ключевым атрибутом (таким как номер транзакции) для измерения. Это создает связь «один к одному» между измерением и фактами в таблице фактов.  
  
  

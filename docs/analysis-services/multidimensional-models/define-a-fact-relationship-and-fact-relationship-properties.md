---
title: "Определение связей фактов и свойств связей фактов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: e1e58f9616fc40ad895858a6eb6b3cfa7e0bbed1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Определение связей фактов и свойств связей фактов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]При определении нового измерения куба или новой группы мер, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли связь измерений фактов и установить настройку использования измерения **фактов**. Связь измерений фактов можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов. Связь фактов между измерением и группой мер имеет следующие ограничения.  
  
-   Измерение куба может иметь только одну связь фактов с конкретной группой мер.  
  
-   Измерение куба может иметь отдельные связи фактов с несколькими группами мер.  
  
-   Атрибут гранулярности для связи должен быть ключевым атрибутом (таким как номер транзакции) для измерения. Это создает связь «один к одному» между измерением и фактами в таблице фактов.  
  
  

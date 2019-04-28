---
title: Определение связей фактов и свойств связей фактов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6663b3a488ff073c823ad8f67ef3a1d120c4a268
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62700065"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Определение связей фактов и свойств связей фактов
  При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли связь измерений фактов, и установить настройку использования измерения, равной `Fact`. Связь измерений фактов можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов. Связь фактов между измерением и группой мер имеет следующие ограничения.  
  
-   Измерение куба может иметь только одну связь фактов с конкретной группой мер.  
  
-   Измерение куба может иметь отдельные связи фактов с несколькими группами мер.  
  
-   Атрибут гранулярности для связи должен быть ключевым атрибутом (таким как номер транзакции) для измерения. Это создает связь «один к одному» между измерением и фактами в таблице фактов.  
  
  

---
title: Указание ключа и измерения типа (мастер измерений) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ce08115251beee6dc71509bc4d3a53420ecd678
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180128"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Указание ключа и типа измерения (мастер измерений)
  На странице **Определение ключа и типа измерения** можно определить ключевой атрибут измерения и указать, является ли измерение медленно меняющимся измерением (SCD).  
  
> [!NOTE]  
>  Эта страница отображается, только если на странице **Выбор метода построения** выбран параметр **Построить измерение без использования источника данных** и если на странице **Выбор типа измерения** выбрано **Стандартное измерение** .  
  
## <a name="options"></a>Параметры  
 **Ключевой атрибут**  
 Выберите атрибут, который будет ключевым атрибутом для измерения.  
  
> [!NOTE]  
>  Если для измерения не определены никакие атрибуты, единственным значением, доступным для этого параметра, является **Создать ключевой атрибут автоматически** . Это значение недоступно, если для измерения определены какие-либо атрибуты.  
  
 **Это изменяющееся измерение**  
 Этот параметр указывает, что измерение является медленно меняющимся измерением. При выборе этого параметра создаются новые столбцы и атрибуты, которые могут использоваться для отслеживания перемещения элементов в иерархиях измерения с течением времени.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера измерений](dimension-wizard-f1-help.md)   
 [Измерения &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
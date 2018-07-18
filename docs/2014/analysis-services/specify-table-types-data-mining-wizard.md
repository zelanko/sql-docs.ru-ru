---
title: Определение типов таблиц (мастер интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c753554dcab61c10bacaf4c118d1781ba3d157b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159075"
---
# <a name="specify-table-types-data-mining-wizard"></a>Определение типов таблиц (мастер интеллектуального анализа данных)
  Страница **Определение типов таблиц** используется для идентификации таблиц, используемых для определения структуры интеллектуального анализа данных. Если таблица не выбрана, она не будет использоваться для определения структуры интеллектуального анализа данных.  
  
> [!NOTE]  
>  Таблицы можно добавлять позже на вкладке **Структура интеллектуального анализа данных** в окне **Конструктор интеллектуального анализа данных**.  
  
 **Дополнительные сведения:** [Вложенные таблицы (службы Analysis Services — интеллектуальный анализ данных)](data-mining/nested-tables-analysis-services-data-mining.md), [Мастер интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](data-mining/data-mining-wizard-analysis-services-data-mining.md) и [Создание реляционной структуры интеллектуального анализа данных](data-mining/create-a-relational-mining-structure.md).  
  
## <a name="options"></a>Параметры  
 **Таблицы**  
 Отображает таблицы в представлении источника данных, выбранном на странице **Выбор представления источников данных** данного мастера.  
  
 **Вариант**  
 Выберите таблицу для использования ее в качестве таблицы вариантов.  
  
 **Вложенные**  
 Выберите таблицы для использования в качестве вложенных таблиц.  
  
> [!NOTE]  
>  У этих таблиц должна быть связь «многие к одному» с таблицей вариантов, а не «один-ко-многим». Необходимо определить эту связь в представлении источника данных, прежде чем можно будет выбрать таблицу в качестве вложенной.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Выберите представление источника данных &#40;мастер интеллектуального анализа данных&#41;](select-data-source-view-data-mining-wizard.md)   
 [Определение обучающих данных &#40;мастер интеллектуального анализа данных&#41;](specify-the-training-data-data-mining-wizard.md)  
  
  

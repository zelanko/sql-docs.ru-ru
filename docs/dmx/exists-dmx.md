---
title: "Существует (DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exists
dev_langs:
- DMX
helpviewer_keywords:
- Exists function
ms.assetid: 3b54dd93-f0a8-4f9a-96ae-a38bf977dda1
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a42c5690b8c80ec752490605e3c3243ee78029de
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="exists-dmx"></a>Exists (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает **true** указанный вложенный запрос возвращает хотя бы одна строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *вложенный запрос*  
 Инструкция SELECT вида SELECT * FROM \<имя столбца > [ГДЕ \<список предикатов >].  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **true** Если результирующего набора, возвращаемого вложенным запросом содержит по крайней мере одну строку; в противном случае возвращает **false**.  
  
## <a name="remarks"></a>Замечания  
 Перед ключевым словом EXISTS можно использовать ключевое слово NOT, например `WHERE NOT EXISTS (<subquery>)`.  
  
 Список столбцов, добавленный к аргументу подзапроса EXISTS, не имеет значения: функция проверяет только существование строки, отвечающей условиям.  
  
## <a name="examples"></a>Примеры  
 Для проверки условий во вложенной таблице можно использовать ключевые слова EXISTS и NOT EXISTS. Это полезно при создании фильтра, управляющего данными, которые использовались для обучения или проверки модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Следующий пример основан на `[Association]` структуры интеллектуального анализа данных и модели интеллектуального анализа данных, созданную в [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает только варианты, в которых заказчик приобрел хотя бы один ремонтный комплект.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Другой способ просмотреть те же данные, возвращаемые этим запросом — открыть модель в средстве просмотра взаимосвязей, щелкните правой кнопкой набор элементов **Patch kit = Existing**выберите **детализация** , а затем установите **только варианты модели**.  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Синтаксис фильтра модели и примеры &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  


---
description: Exists (расширения интеллектуального анализа данных)
title: Exists (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0fa41dfff8edc6ddddeb420027a436f235e54a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353340"
---
# <a name="exists-dmx"></a>Exists (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Возвращает **значение true** , если указанный вложенный запрос возвращает хотя бы одну строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *subquery*  
 Инструкция SELECT в форме SELECT * FROM \<column name> [Where \<predicate list> ].  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **значение true** , если результирующий набор, возвращаемый вложенным запросом, содержит по крайней мере одну строку. в противном случае возвращает **значение false**.  
  
## <a name="remarks"></a>Remarks  
 Перед ключевым словом EXISTS можно использовать ключевое слово NOT, например `WHERE NOT EXISTS (<subquery>)`.  
  
 Список столбцов, добавленный к аргументу подзапроса EXISTS, не имеет значения: функция проверяет только существование строки, отвечающей условиям.  
  
## <a name="examples"></a>Примеры  
 Для проверки условий во вложенной таблице можно использовать ключевые слова EXISTS и NOT EXISTS. Это полезно при создании фильтра, управляющего данными, которые использовались для обучения или проверки модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 Следующий пример основан на структуре и модели интеллектуального анализа данных `[Association]` , созданных в [учебнике по основам интеллектуального анализа](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает только варианты, в которых заказчик приобрел хотя бы один ремонтный комплект.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Другим способом просмотра тех же данных, которые возвращаются этим запросом, является открытие модели в средстве просмотра взаимосвязей, щелкните правой кнопкой мыши набор элементов **patching Kit = existing**, выберите параметр **Детализация** и выберите **только варианты модели**.  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Синтаксис и примеры фильтра модели (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining)  
  
  

---
title: Exists (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0197417dfef604f3cb90b5fa032dae892de272c7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68889047"
---
# <a name="exists-dmx"></a>Exists (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает **значение true** , если указанный вложенный запрос возвращает хотя бы одну строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *вложенный запрос*  
 Инструкция SELECT в форме SELECT * FROM \<имя столбца> [Where \<список предикатов>].  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **значение true** , если результирующий набор, возвращаемый вложенным запросом, содержит по крайней мере одну строку. в противном случае возвращает **значение false**.  
  
## <a name="remarks"></a>Remarks  
 Перед ключевым словом EXISTS можно использовать ключевое слово NOT, например `WHERE NOT EXISTS (<subquery>)`.  
  
 Список столбцов, добавленный к аргументу подзапроса EXISTS, не имеет значения: функция проверяет только существование строки, отвечающей условиям.  
  
## <a name="examples"></a>Примеры  
 Для проверки условий во вложенной таблице можно использовать ключевые слова EXISTS и NOT EXISTS. Это полезно при создании фильтра, управляющего данными, которые использовались для обучения или проверки модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 Следующий пример основан на `[Association]` структуре и модели интеллектуального анализа данных, созданных в [учебнике по основам интеллектуального анализа](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает только варианты, в которых заказчик приобрел хотя бы один ремонтный комплект.  
  
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
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Синтаксис и примеры фильтра модели (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining)  
  
  

---
title: Существует (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 936612dba4f466c5bc78f20f5a3ea07954a20a1c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37998586"
---
# <a name="exists-dmx"></a>Exists (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает **true** указанный вложенный запрос возвращает хотя бы одна строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *subquery*  
 Инструкция SELECT вида SELECT * FROM \<имя столбца > [ГДЕ \<список предикатов >].  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **true** Если результирующего набора, возвращаемого вложенным запросом, содержит по крайней мере одну строку; в противном случае возвращает **false**.  
  
## <a name="remarks"></a>Примечания  
 Перед ключевым словом EXISTS можно использовать ключевое слово NOT, например `WHERE NOT EXISTS (<subquery>)`.  
  
 Список столбцов, добавленный к аргументу подзапроса EXISTS, не имеет значения: функция проверяет только существование строки, отвечающей условиям.  
  
## <a name="examples"></a>Примеры  
 Для проверки условий во вложенной таблице можно использовать ключевые слова EXISTS и NOT EXISTS. Это полезно при создании фильтра, управляющего данными, которые использовались для обучения или проверки модели интеллектуального анализа данных. Дополнительные сведения см. в разделе [Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Следующий пример построен на основе `[Association]` структуры интеллектуального анализа данных и модели интеллектуального анализа данных, созданный в [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает только варианты, в которых заказчик приобрел хотя бы один ремонтный комплект.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Еще один способ просмотреть те же данные, возвращаемые этим запросом является открыть модель в средстве просмотра взаимосвязей, щелкните правой кнопкой набор элементов **Patch kit = существующий**выберите **детализация** параметр, а затем Выберите **только варианты модели**.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Модели, синтаксис и примеры фильтров &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  

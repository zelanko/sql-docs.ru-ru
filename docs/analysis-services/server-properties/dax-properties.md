---
title: Свойства DAX | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9bab5be6922de312c56bc67626ee5d22fc41ffb9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dax-properties"></a>Свойства DAX
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
   Раздел DAX файла msmdsrv.ini содержит параметры, используемые для управления поведением запросов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], такие как верхний предел числа строк, возвращаемых в результирующем наборе запроса DAX.

  Для очень крупных наборов строк, например тех, которые возвращаются в моделях DirectQuery, значения по умолчанию, равного одному миллиону строк, может быть недостаточно. На необходимость корректировки предела указывает появление следующей ошибки: "Набор результатов запроса к внешнему источнику данных превышает максимально допустимое количество строк: 1000000".

Чтобы увеличить верхний предел, задайте параметр конфигурации **MaxIntermediateRowSize** . Потребуется вручную добавить весь элемент в раздел DAX файла конфигурации. Параметр отсутствует в файле, пока не будет добавлен.

## <a name="configuration-snippet"></a>Фрагмент кода конфигурации

```
<ConfigurationSettings>
. . .
<DAX>
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . .
```

## <a name="property-descriptions"></a>Описание свойств

Настройка |Значение |Описание
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Максимальное число строк, возвращаемых в запросе DAX. Вручную добавьте эту запись в файл msmdsrv.ini и увеличьте показатель, если значение по умолчанию слишком мало.
PredicateCheckSpoolCardinalityThreshold| 5000 | Дополнительное свойство, которое следует изменять только под руководством службы поддержки Майкрософт.

Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).

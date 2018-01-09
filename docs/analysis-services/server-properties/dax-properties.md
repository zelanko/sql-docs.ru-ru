---
title: "Свойства DAX | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: "6"
author: HeidiSteen
ms.author: heidist
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 76ffc0da4e8d56b4bb37b0be5278e458ac6fb043
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dax-properties"></a>Свойства DAX
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]DAX раздел msmdsrv.ini содержит параметры, используемые для управления определенными параметрами запроса в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], такие как верхний предел на число строк, возвращаемых в результирующем наборе запроса DAX. 
  
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

Настройка |Значение |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Максимальное число строк, возвращаемых в запросе DAX. Вручную добавьте эту запись в файл msmdsrv.ini и увеличьте показатель, если значение по умолчанию слишком мало. 
PredicateCheckSpoolCardinalityThreshold| 5000 | Дополнительное свойство, которое следует изменять только под руководством службы поддержки Майкрософт.

Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md). 

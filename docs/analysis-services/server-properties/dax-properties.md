---
title: "Свойства DAX | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: 6
author: "HeidiSteen"
ms.author: "heidist"
manager: "erikre"
caps.handback.revision: 6
---
# Свойства DAX
   Раздел DAX файла msmdsrv.ini содержит параметры, используемые для управления поведением запросов в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], такие как верхний предел числа строк, возвращаемых в результирующем наборе запроса DAX. 
  
  Для очень крупных наборов строк, например тех, которые возвращаются в моделях DirectQuery, значения по умолчанию, равного одному миллиону строк, может быть недостаточно. На необходимость корректировки предела указывает появление следующей ошибки: "Набор результатов запроса к внешнему источнику данных превышает максимально допустимое количество строк: 1000000".
 
Чтобы увеличить верхний предел, задайте параметр конфигурации **MaxIntermediateRowSize**. Потребуется вручную добавить весь элемент в раздел DAX файла конфигурации. Параметр отсутствует в файле, пока не будет добавлен.
  
## Фрагмент кода конфигурации

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

## Описание свойств

Настройка |Значение |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Максимальное число строк, возвращаемых в запросе DAX. Вручную добавьте эту запись в файл msmdsrv.ini и увеличьте показатель, если значение по умолчанию слишком мало. 
PredicateCheckSpoolCardinalityThreshold| 5000 | Дополнительное свойство, которое следует изменять только под руководством службы поддержки Майкрософт.

Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md). 
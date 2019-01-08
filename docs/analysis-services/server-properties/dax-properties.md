---
title: Службы Analysis Services свойства DAX | Документация Майкрософт
ms.date: 10/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 20a6df833f8c525c24abdf3bb51278d0067db951
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071901"
---
# <a name="dax-properties"></a>Свойства DAX
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

   Раздел DAX файла msmdsrv.ini содержит параметры, используемые для управления поведением запросов в службах Analysis Services, такие как верхний предел на число строк, возвращаемых в результирующем наборе запроса DAX.

  Для очень крупных наборов строк, например тех, которые возвращаются в моделях DirectQuery, значения по умолчанию, равного одному миллиону строк, может быть недостаточно. Вы будете знать, должен ли ограничение настройки, если вы получаете эту ошибку: «Результирующий набор запроса к внешнему источнику данных превышает максимально допустимый размер строк: 1000000".»

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

Параметр |Значение |Описание
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Максимальное число строк, возвращаемых в запросе DAX. Вручную добавьте эту запись в файл msmdsrv.ini и увеличьте показатель, если значение по умолчанию слишком мало.
PredicateCheckSpoolCardinalityThreshold| 5000 | Дополнительное свойство, которое следует изменять только под руководством службы поддержки Майкрософт.

Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).

---
title: Сведения о привязке запроса (диалоговое окно «Источник секции») (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539756"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Сведения о привязке запроса (диалоговое окно «Источник секции») (службы Analysis Services — многомерные данные)
  Используйте параметр **Привязка запроса** в диалоговом окне **Источник секции** , чтобы указать запрос, предоставляющий данные для секции. Можно отобразить эту панель, выбрав параметр **Привязка запроса** в качестве значения **Типа привязки** в диалоговом окне **Источник секции** .  
  
## <a name="options"></a>Варианты  
 **Источник данных**  
 Выберите источник данных, в котором должен выполниться запрос, чтобы обеспечить секцию данными фактов.  
  
 **Запрос**  
 Введите или измените инструкцию SQL, используемую для получения данных фактов в процессе обработки секции.  
  
> [!IMPORTANT]  
>  Указав предложение WHERE, для этой секции можно использовать вложенный набор записей. Данное действие необходимо во избежание дублирования данных в случае, если несколько параллельных секций функционируют с помощью единственной таблицы фактов. Дополнительные сведения см. в разделе [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Проверить**  
 Щелкните, чтобы проверить, является ли инструкция в поле **Запрос** допустимой инструкцией SQL.  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно «Источник секции» &#40;Analysis Services многомерных данных&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  

---
title: (Диалоговое окно «Источник секции») сведения о привязке запроса (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e9a9fc76282ebd231e18aec24fe6a9d28650100
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195028"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Сведения о привязке запроса (диалоговое окно «Источник секции») (службы Analysis Services — многомерные данные)
  Используйте параметр **Привязка запроса** в диалоговом окне **Источник секции** , чтобы указать запрос, предоставляющий данные для секции. Можно отобразить эту панель, выбрав параметр **Привязка запроса** в качестве значения **Типа привязки** в диалоговом окне **Источник секции** .  
  
## <a name="options"></a>Параметры  
 **Источник данных**  
 Выберите источник данных, в котором должен выполниться запрос, чтобы обеспечить секцию данными фактов.  
  
 **Запрос**  
 Введите или измените инструкцию SQL, используемую для получения данных фактов в процессе обработки секции.  
  
> [!IMPORTANT]  
>  Указав предложение WHERE, для этой секции можно использовать вложенный набор записей. Данное действие необходимо во избежание дублирования данных в случае, если несколько параллельных секций функционируют с помощью единственной таблицы фактов. Дополнительные сведения см. в разделе [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Проверить**  
 Щелкните, чтобы проверить, является ли инструкция в поле **Запрос** допустимой инструкцией SQL.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно источника секции &#40;службы Analysis Services — многомерные данные&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
---
title: (Partition Source Dialog Box) сведения о привязке запроса (службы Analysis Services — многомерные данные) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 604a42cc0b3519f1034733e12f72dc1a7c969ce6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070567"
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
 [Окно выбора источника секции &#40;службы Analysis Services — многомерные данные&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  

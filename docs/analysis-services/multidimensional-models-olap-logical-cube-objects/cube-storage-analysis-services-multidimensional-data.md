---
title: Куб хранилища (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 05ff45fa98b578fce295ab2113abf301bc3b78ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181002"
---
# <a name="cube-storage-analysis-services---multidimensional-data"></a>Хранилище кубов (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В хранилище могут содержаться либо только метаданные куба, либо все исходные данные из таблицы фактов и все агрегаты, определенные связанными с группой мер измерениями. Объем хранимых данных зависит от выбранного режима хранения и количества агрегатов. Объем сохраняемых данных непосредственно влияет на производительность запросов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют несколько методов минимизации дискового пространства, необходимого для хранения данных и агрегатов куба.  
  
-   Параметры хранилища позволяют выбрать режим хранения и наиболее подходящее место хранения данных куба.  
  
-   Применяются сложные алгоритмы, эффективно рассчитывающие агрегаты для минимизации хранилища, без уменьшения скорости.  
  
-   Под пустые ячейки место не выделяется.  
  
 Хранилище определяется последовательно для каждой секции; для каждой группы мер куба существует, по крайней мере, одна секция. Дополнительные сведения см. в разделе [секций &#40;службы Analysis Services — многомерные данные&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [режимы хранения и обработки](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md), [мер и групп мер](../../analysis-services/multidimensional-models/measures-and-measure-groups.md), и [Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).  
  
## <a name="partition-storage"></a>Partition Storage  
 Хранилище для группы мер может быть разбито на несколько секций. Секции позволяют распределять группы мер между отдельными сегментами на одном или нескольких серверах, а также оптимизировать производительность хранилища и обработки запросов. У каждой секции в группе мер может быть свой источник данных и собственные параметры хранения.  
  
 Источник данных секции определяется при ее создании. Источник данных существующей секции можно изменить. Группу мер можно разбить на секции по вертикали или по горизонтали. При вертикальном разбиении каждая секция образуется на основе отфильтрованного представления одной исходной таблицы. Например, если группа мер основывается на одной таблице, содержащей данные за несколько лет, можно на каждый год выделить отдельную секцию. Напротив, при горизонтальном секционировании каждая секция основывается на отдельной таблице. Метод горизонтального секционирования применим в том случае, когда данные за каждый год хранятся в отдельной таблице источника данных.  
  
 Секции изначально создаются с параметрами хранения группы мер, которой они принадлежат. Параметры хранилища определяют способ хранения подробных данных и агрегатов. Данные могут храниться в многомерном формате на экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]или в реляционном формате на исходном сервере, причем способы хранения данных можно сочетать друг с другом. Параметры хранилища управляют также упреждающим кэшированием, которое применяется для автоматического распространения изменений исходных данных на многомерные данные, хранящиеся на сервере служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Секции куба для пользователя невидимы, однако выбор параметров хранилища для различных секций может повлиять на оперативность данных, объем используемого места на диске и на производительность запроса. Секции могут храниться на нескольких экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это обеспечивает подход к хранению куба с использованием кластеризации и распределяет рабочую нагрузку между серверами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в разделе [режимы хранения и обработки](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md), [удаленных секций](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md), и [секций &#40;службы Analysis Services — многомерные данные&#41; ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md).  
  
## <a name="linked-measure-groups"></a>Связанные группы мер  
 Хранение нескольких копий куба на различных экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]может потребовать довольно много места на диске, но можно этого избежать, заменив копии группы мер связанными группами мер. Связанная группа мер образуется на основе группы мер куба в другой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или в другом экземпляре той же базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Связанная группа мер может также использоваться со связанными измерениями из того же исходного куба. Связанные измерения и группы мер используют агрегаты исходного куба и не требуют дополнительного пространства. Таким образом, помещение исходных группы мер и измерений в одну базу данных и создание связанных групп мер и измерений в кубе другой базы данных позволяет сэкономить место на диске. Дополнительные сведения см. в разделе [Linked Measure Groups](../../analysis-services/multidimensional-models/linked-measure-groups.md).  
  
## <a name="see-also"></a>См. также  
 [Агрегаты и статистические схемы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  

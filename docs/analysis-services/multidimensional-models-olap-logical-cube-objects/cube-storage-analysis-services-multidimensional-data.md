---
title: "Куб хранения данных (службы Analysis Services — многомерные данные) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- measure groups [Analysis Services], cubes
- cubes [Analysis Services], storage
- linked measure groups [Analysis Services]
- storing data [Analysis Services], cubes
- partitions [Analysis Services], cubes
- storage [Analysis Services], cubes
ms.assetid: 1b1ad360-9a9b-4996-bee9-84238a2bb4ac
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 082e54f8ebaf83609c8f90b37e41657cb26da1f7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cube-storage-analysis-services---multidimensional-data"></a>Хранилище кубов (службы Analysis Services — многомерные данные)
  В хранилище могут содержаться либо только метаданные куба, либо все исходные данные из таблицы фактов и все агрегаты, определенные связанными с группой мер измерениями. Объем хранимых данных зависит от выбранного режима хранения и количества агрегатов. Объем сохраняемых данных непосредственно влияет на производительность запросов. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют несколько методов минимизации дискового пространства, необходимого для хранения данных и агрегатов куба:  
  
-   Параметры хранилища позволяют выбрать режим хранения и наиболее подходящее место хранения данных куба.  
  
-   Применяются сложные алгоритмы, эффективно рассчитывающие агрегаты для минимизации хранилища, без уменьшения скорости.  
  
-   Под пустые ячейки место не выделяется.  
  
 Хранилище определяется последовательно для каждой секции; для каждой группы мер куба существует, по крайней мере, одна секция. Дополнительные сведения см. в разделе [секций &#40; Analysis Services — многомерные данные &#41; ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [Секции режимы хранения и обработка](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md), [меры и группы мер](../../analysis-services/multidimensional-models/measures-and-measure-groups.md), и [Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md) .  
  
## <a name="partition-storage"></a>Partition Storage  
 Хранилище для группы мер может быть разбито на несколько секций. Секции позволяют распределять группы мер между отдельными сегментами на одном или нескольких серверах, а также оптимизировать производительность хранилища и обработки запросов. У каждой секции в группе мер может быть свой источник данных и собственные параметры хранения.  
  
 Источник данных секции определяется при ее создании. Источник данных существующей секции можно изменить. Группу мер можно разбить на секции по вертикали или по горизонтали. При вертикальном разбиении каждая секция образуется на основе отфильтрованного представления одной исходной таблицы. Например, если группа мер основывается на одной таблице, содержащей данные за несколько лет, можно на каждый год выделить отдельную секцию. Напротив, при горизонтальном секционировании каждая секция основывается на отдельной таблице. Метод горизонтального секционирования применим в том случае, когда данные за каждый год хранятся в отдельной таблице источника данных.  
  
 Секции изначально создаются с параметрами хранения группы мер, которой они принадлежат. Параметры хранилища определяют способ хранения подробных данных и агрегатов. Данные могут храниться в многомерном формате на экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или в реляционном формате на исходном сервере, причем способы хранения данных можно сочетать друг с другом. Параметры хранилища управляют также упреждающим кэшированием, которое применяется для автоматического распространения изменений исходных данных на многомерные данные, хранящиеся на сервере служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Секции куба для пользователя невидимы, однако выбор параметров хранилища для различных секций может повлиять на оперативность данных, объем используемого места на диске и на производительность запроса. Секции могут храниться на нескольких экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это обеспечивает подход к хранению куба с использованием кластеризации и распределяет рабочую нагрузку между серверами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения см. в разделе [режимы хранения секции и обработка](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md), [удаленных секций](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md), и [секций &#40; Analysis Services — многомерные данные &#41; ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md).  
  
## <a name="linked-measure-groups"></a>Связанные группы мер  
 Хранение нескольких копий куба на различных экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может потребовать довольно много места на диске, но можно этого избежать, заменив копии группы мер связанными группами мер. Связанная группа мер основан на группу мер в кубе в другом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных на том же или другом экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Связанная группа мер может также использоваться со связанными измерениями из того же исходного куба. Связанные измерения и группы мер используют агрегаты исходного куба и не требуют дополнительного пространства. Таким образом, помещение исходных группы мер и измерений в одну базу данных и создание связанных групп мер и измерений в кубе другой базы данных позволяет сэкономить место на диске. Дополнительные сведения см. в разделе [связанные группы мер](../../analysis-services/multidimensional-models/linked-measure-groups.md).  
  
## <a name="see-also"></a>См. также:  
 [Агрегаты и статистические схемы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  

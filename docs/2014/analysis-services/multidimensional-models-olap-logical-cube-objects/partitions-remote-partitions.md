---
title: Удаленные секции | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- MasterDataSourceID property
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3643bda36793f95389d1aad86a2cd42a77d606d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251316"
---
# <a name="remote-partitions"></a>Удаленные секции
  Данные удаленной секции хранятся на другом экземпляре Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] чем экземпляр, содержащий определения (метаданные) секции и ее родительского куба. Управление удаленной секцией выполняется на том же экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], на котором определены секция и ее родительский куб.  
  
> [!NOTE]  
>  Чтобы сохранить удаленную секцию, на компьютере должен быть экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] установлен и может работать один и тот же уровень пакета обновления в виде экземпляра, где определена секция. Удаленные секции экземпляров более ранних версий служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживаются.  
  
 При включении удаленных секций в группу мер происходит распределение памяти и загрузки ЦП по всем секциям группы мер. Например, во время обработки удаленной секции, отдельно или как часть процесса обработки ее родительского куба, максимальная загрузка памяти ЦП для данной секции приходится на удаленный экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Куб, который содержит удаленные секции, может содержать измерения, доступные для записи. Однако это может влиять на производительность этого куба. Дополнительные сведения о записи измерений, см. в разделе [измерениях](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="storage-modes-for-remote-partitions"></a>Режимы хранения для удаленных секций  
 Удаленные секции могут использовать любой из перечисленных ниже типов хранилищ, применяемых локальными секциями: многомерный OLAP (MOLAP), гибридный OLAP (HOLAP) или реляционный OLAP (ROLAP). Кроме того, удаленные секции могут использовать упреждающее кэширование. В зависимости от режима хранения удаленной секции на удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранятся следующие данные.  
  
|||  
|-|-|  
|Тип хранения|Данные |  
|MOLAP|Статистические схемы секции и копия исходных данных секции|  
|HOLAP|Статистические схемы секций|  
|ROLAP|Данные секции отсутствуют|  
  
 Если в группе мер содержится несколько секций MOLAP или HOLAP, хранимых на нескольких экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], то куб распределяет данные группы мер между указанными экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="merging-remote-partitions"></a>Слияние удаленных секций  
 Удаленные секции можно объединять только с удаленными секциями, хранимыми на том же удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения о слиянии секций см. в разделе [слияние секций в службах Analysis Services &#40;службы SSAS — многомерные&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).  
  
## <a name="archiving-and-restoring-remote-partitions"></a>Архивация и восстановление удаленных секций  
 Данные удаленных секций можно архивировать или восстанавливать, когда архивируется или восстанавливается хранящая их база данных. Если восстановление базы данных выполняется без восстановления удаленной секции, то прежде чем использовать данные секции, необходимо обработать удаленную секцию. Дополнительные сведения об архивации и восстановлении баз данных см. в разделе [резервное копирование и восстановление из базы данных Analysis Services](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и управление удаленной секцией &#40;служб Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [Обработка служб Analysis Services объектов](../multidimensional-models/processing-analysis-services-objects.md)  
  
  

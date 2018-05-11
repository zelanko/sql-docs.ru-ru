---
title: Удаленные секции | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 218b3b1b18283463ded4693abeba70a063fe1499
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="partitions---remote-partitions"></a>Секции — удаленных секций
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Данные удаленной секции хранятся в другом экземпляре Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] от экземпляра, содержащего определения (метаданные) секции и ее родительского куба. Управление удаленной секцией выполняется на том же экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], на котором определены секция и ее родительский куб.  
  
> [!NOTE]  
>  Чтобы сохранить удаленную секцию, на компьютере должен быть экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] установить и использовать один и тот же уровень пакета обновления от экземпляра, где определена секция. Удаленные секции экземпляров более ранних версий служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживаются.  
  
 При включении удаленных секций в группу мер происходит распределение памяти и загрузки ЦП по всем секциям группы мер. Например, во время обработки удаленной секции, отдельно или как часть процесса обработки ее родительского куба, максимальная загрузка памяти ЦП для данной секции приходится на удаленный экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Куб, который содержит удаленные секции, может содержать измерения, доступные для записи. Однако это может влиять на производительность этого куба. Дополнительные сведения о записи измерений см. в разделе [измерениях](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
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
 Удаленные секции можно объединять только с удаленными секциями, хранимыми на том же удаленном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения о слиянии секций см. в разделе [слияние секций в службах Analysis Services &#40;службы SSAS — многомерные&#41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).  
  
## <a name="archiving-and-restoring-remote-partitions"></a>Архивация и восстановление удаленных секций  
 Данные удаленных секций можно архивировать или восстанавливать, когда архивируется или восстанавливается хранящая их база данных. Если восстановление базы данных выполняется без восстановления удаленной секции, то прежде чем использовать данные секции, необходимо обработать удаленную секцию. Дополнительные сведения об архивации и восстановлении баз данных см. в разделе [резервного копирования и восстановления для базы данных Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и управление удаленной секцией & #40; Службы Analysis Services & #41;](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [Обработка служб Analysis Services объектов](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md)  
  
  

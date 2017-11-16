---
title: "Задание свойств многомерной базы данных (службы Analysis Services) | Документы Microsoft"
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
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Analysis Services], databases
ms.assetid: a8be5b3f-3148-448a-976c-7222705155d9
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8a63ce60ecba071b10f3b36ea32d2e9bef9109cb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-multidimensional-database-properties-analysis-services"></a>Задание свойств многомерной базы данных (службы Analysis Services)
  Предусмотрен целый ряд свойств базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые можно настроить в конструкторе базы данных служб среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
 В этом конструкторе можно выполнить следующие типы задач.  
  
-   При подключении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме в сети имя базы данных можно изменить [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . При работе в режиме проекта имя базы данных можно изменить для следующего развертывания проекта. Дополнительные сведения см. в разделах [Переименование многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md) и [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
-   Можно предоставить описание базы данных, которое будет представлено пользователям. Также можно просмотреть имя базы данных, но не изменить его. Чтобы изменить имя базы данных, необходимо изменить свойства проекта.  
  
-   Можно предоставить перевод имени и описания базы данных на один или несколько языков. Дополнительные сведения см. в разделе [Переводы куба](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Переводы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)и [Поддержка параметров перевода в службах Analysis Services](../../analysis-services/translation-support-in-analysis-services.md).  
  
-   Можно просматривать и изменять сопоставления типа учетной записи по умолчанию. Сопоставления типа учетной записи применяются тогда, когда одна или несколько мер используют статистическую функцию *ByAccount* . Для каждого типа учетной записи можно указать псевдоним и изменить статистическую функцию по умолчанию, связанную с данным типом учетной записи. Дополнительные сведения об изменении агрегата по умолчанию см. в разделе [Определение полуаддитивного режима](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md).  
  
## <a name="database-properties"></a>Свойства базы данных  
 В окне «Свойства» можно настроить многие свойства базы данных, помимо указанных выше.  
  
|Свойство|Description|  
|--------------|-----------------|  
|Префикс статистической схемы|Общий префикс, который может использоваться для имен агрегатов всех секций базы данных. Дополнительные сведения см. в разделе [Элемент AggregationPrefix (ASSL)](../../analysis-services/scripting/properties/aggregationprefix-element-assl.md).|  
|Параметры сортировки|Если проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывается на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , то база данных наследует свойство Collation севера, если не указать другое значение.|  
|DataSourceImpersonationInfo|Указывает режим олицетворения по умолчанию для всех объектов источника данных в базе данных. Это режим, который использует служба [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при обработке объектов, синхронизации серверов и выполнении инструкций интеллектуального анализа данных OpenQuery и SystemOpenSchema.|  
|Предполагаемый размер|Содержит предполагаемый размер файлов базы данных на диске. Если данные хранятся в нескольких местах, оценка будет ограничена только файлами данных, хранящимися в папке базы данных.<br /><br /> Также в качестве основы для оценки памяти можно использовать**EstimatedSize** . Обычно требования к памяти больше размера данных на диске из-за наличия дополнительных структур данных, создаваемых при загрузке базы данных в память.<br /><br /> Для дальнейшей оценки требований к памяти можно также воспользоваться диспетчером задач, чтобы сравнить память процесса служб Analysis Services до и после обработки базы данных и отследить задействованный объем памяти в качестве метода анализа требований базы данных к памяти.|  
|Язык|При развертывании проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] база данных унаследует свойство Language сервера, если не указать другое значение.|  
|MasterDataSource ID|Используется удаленными секциями. Дополнительные сведения см. в разделе [Remote Partitions](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).|  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Свойства базы данных" (службы SSAS — многомерные)](http://msdn.microsoft.com/library/70f000b7-917f-4699-b142-7a0d13ff767c)   
 [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  


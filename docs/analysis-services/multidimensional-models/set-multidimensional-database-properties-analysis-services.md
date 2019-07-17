---
title: Задание свойств многомерной базы данных (службы Analysis Services) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 489d738ac8d654477687528ad64c2fed76877dde
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208496"
---
# <a name="set-multidimensional-database-properties-analysis-services"></a>Задание свойств многомерной базы данных (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Предусмотрен целый ряд свойств базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые можно настроить в конструкторе базы данных служб среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
 В этом конструкторе можно выполнить следующие типы задач.  
  
-   При подключении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме в сети имя базы данных можно изменить [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . При работе в режиме проекта имя базы данных можно изменить для следующего развертывания проекта. Дополнительные сведения см. в разделах [Переименование многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md) и [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
-   Можно предоставить описание базы данных, которое будет представлено пользователям. Также можно просмотреть имя базы данных, но не изменить его. Чтобы изменить имя базы данных, необходимо изменить свойства проекта.  
  
-   Можно предоставить перевод имени и описания базы данных на один или несколько языков. Дополнительные сведения см. в разделе [Переводы куба](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Переводы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)и [Поддержка параметров перевода в службах Analysis Services](../../analysis-services/translation-support-in-analysis-services.md).  
  
-   Можно просматривать и изменять сопоставления типа учетной записи по умолчанию. Сопоставления типа учетной записи применяются тогда, когда одна или несколько мер используют статистическую функцию *ByAccount* . Для каждого типа учетной записи можно указать псевдоним и изменить статистическую функцию по умолчанию, связанную с данным типом учетной записи. Дополнительные сведения об изменении агрегата по умолчанию см. в разделе [Определение полуаддитивного режима](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md).  
  
## <a name="database-properties"></a>Свойства базы данных  
 В окне «Свойства» можно настроить многие свойства базы данных, помимо указанных выше.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|Префикс статистической схемы|Общий префикс, который может использоваться для имен агрегатов всех секций базы данных. Дополнительные сведения см. в разделе [Элемент AggregationPrefix (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/aggregationprefix-element-assl).|  
|Параметры сортировки|Если проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывается на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , то база данных наследует свойство Collation севера, если не указать другое значение.|  
|DataSourceImpersonationInfo|Указывает режим олицетворения по умолчанию для всех объектов источника данных в базе данных. Это режим, который использует служба [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при обработке объектов, синхронизации серверов и выполнении инструкций интеллектуального анализа данных OpenQuery и SystemOpenSchema.|  
|Предполагаемый размер|Содержит предполагаемый размер файлов базы данных на диске. Если данные хранятся в нескольких местах, оценка будет ограничена только файлами данных, хранящимися в папке базы данных.<br /><br /> Также в качестве основы для оценки памяти можно использовать**EstimatedSize** . Обычно требования к памяти больше размера данных на диске из-за наличия дополнительных структур данных, создаваемых при загрузке базы данных в память.<br /><br /> Для дальнейшей оценки требований к памяти можно также воспользоваться диспетчером задач, чтобы сравнить память процесса служб Analysis Services до и после обработки базы данных и отследить задействованный объем памяти в качестве метода анализа требований базы данных к памяти.|  
|Язык|При развертывании проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] база данных унаследует свойство Language сервера, если не указать другое значение.|  
|MasterDataSource ID|Используется удаленными секциями. Дополнительные сведения см. в разделе [Remote Partitions](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).|  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Свойства базы данных" (службы SSAS — многомерные)](http://msdn.microsoft.com/library/70f000b7-917f-4699-b142-7a0d13ff767c)   
 [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  

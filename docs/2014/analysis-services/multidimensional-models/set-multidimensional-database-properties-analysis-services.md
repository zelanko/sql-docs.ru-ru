---
title: Задание свойств многомерной базы данных (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], databases
ms.assetid: a8be5b3f-3148-448a-976c-7222705155d9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aa3e1544f625183df3240359aa22b117144244d3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072995"
---
# <a name="set-multidimensional-database-properties-analysis-services"></a>Задание свойств многомерной базы данных (службы Analysis Services)
  Существует ряд [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] свойств базы данных, которые можно настроить в конструкторе [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] баз данных.  
  
 В этом конструкторе можно выполнить следующие типы задач.  
  
-   При подключении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме в сети имя базы данных можно изменить [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . При работе в режиме проекта имя базы данных можно изменить для следующего развертывания проекта. Дополнительные сведения см. в разделах [Переименование многомерной базы данных (службы Analysis Services)](rename-a-multidimensional-database-analysis-services.md) и [Настройка свойств проекта служб Analysis Services (среда SSDT)](configure-analysis-services-project-properties-ssdt.md).  
  
-   Можно предоставить описание базы данных, которое будет представлено пользователям. Также можно просмотреть имя базы данных, но не изменить его. Чтобы изменить имя базы данных, необходимо изменить свойства проекта.  
  
-   Можно предоставить перевод имени и описания базы данных на один или несколько языков. Дополнительные сведения см. в статьях [переводы куба](../multidimensional-models-olap-logical-cube-objects/cube-translations.md), [переводы измерений](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)и [переводы &#40;Analysis Services&#41;](../translations-analysis-services.md).  
  
-   Можно просматривать и изменять сопоставления типа учетной записи по умолчанию. Сопоставления типа учетной записи применяются тогда, когда одна или несколько мер используют статистическую функцию *ByAccount* . Для каждого типа учетной записи можно указать псевдоним и изменить статистическую функцию по умолчанию, связанную с данным типом учетной записи. Дополнительные сведения об изменении агрегата по умолчанию см. в разделе [Определение полуаддитивного режима](define-semiadditive-behavior.md).  
  
## <a name="database-properties"></a>Свойства базы данных  
 В окне «Свойства» можно настроить многие свойства базы данных, помимо указанных выше.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|Префикс статистической схемы|Общий префикс, который может использоваться для имен агрегатов всех секций базы данных. Дополнительные сведения см. в разделе [Элемент AggregationPrefix (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/aggregationprefix-element-assl).|  
|Параметры сортировки|Если проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывается на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , то база данных наследует свойство Collation севера, если не указать другое значение.|  
|DataSourceImpersonationInfo|Указывает режим олицетворения по умолчанию для всех объектов источника данных в базе данных. Это режим, который использует служба [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при обработке объектов, синхронизации серверов и выполнении инструкций интеллектуального анализа данных OpenQuery и SystemOpenSchema.|  
|Предполагаемый размер|Содержит предполагаемый размер файлов базы данных на диске. Если данные хранятся в нескольких местах, оценка будет ограничена только файлами данных, хранящимися в папке базы данных.<br /><br /> Также в качестве основы для оценки памяти можно использовать `EstimatedSize`. Обычно требования к памяти больше размера данных на диске из-за наличия дополнительных структур данных, создаваемых при загрузке базы данных в память.<br /><br /> Для дальнейшей оценки требований к памяти можно также воспользоваться диспетчером задач, чтобы сравнить память процесса служб Analysis Services до и после обработки базы данных и отследить задействованный объем памяти в качестве метода анализа требований базы данных к памяти.|  
|Язык|При развертывании проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] база данных унаследует свойство Language сервера, если не указать другое значение.|  
|MasterDataSource ID|Используется удаленными секциями. Дополнительные сведения см. в разделе [Remote Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).|  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно «Свойства базы данных» &#40;службы SSAS — многомерные&#41;](../database-properties-dialog-box-ssas-multidimensional.md)   
 [Настройка свойств проекта служб Analysis Services (среда SSDT)](configure-analysis-services-project-properties-ssdt.md)  
  
  

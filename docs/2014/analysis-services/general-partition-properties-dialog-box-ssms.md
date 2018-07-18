---
title: Общие (диалоговое окно «Свойства секции») (среда SSMS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.general.f1
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 54ef8ce15795f8744b8ab7d368c05892a2dc850a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170155"
---
# <a name="general-partition-properties-dialog-box-ssms"></a>Страница «Общие» (диалоговое окно «Свойства секции») (среда SSMS)
  Используйте страницу **Общие** диалогового окна **Свойства секции** в среде SQL Server Management Studio, чтобы установить общие свойства секции в группе мер для куба в базе данных служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Идентификатор статистической схемы**|Отображает идентификатор структуры статистической схемы, используемой секцией.|  
|**Префикс агрегата**|Отображает префикс по умолчанию экземпляров статистических схем, содержащихся в секции.|  
|**Отметка времени создания**|Отображает дату и время создания секции.|  
|**Текущий режим хранения**|Отображает текущий режим хранения секции.<br /><br /> Примечание. Этот режим может меняться в зависимости от параметров упреждающего кэширования для секции. Дополнительные сведения об упреждающем кэшировании см. в разделе [Упреждающее кэширование (секции)](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Описание**|Введите, чтобы изменить описание секции.|  
|**Предполагаемое количество строк**|Введите оценочное количество строк в базовом источнике данных, представленном секцией. Это значение используется во время обработки для оценки времени и объема хранилища, требуемых для обработки секции.|  
|**Предполагаемый размер**|Отображается предполагаемый размер секции.|  
|**Идентификатор**|Отображается идентификатор секции.|  
|**Последняя обработка**|Отображает дату и время последней обработки секции.|  
|**Последнее обновление схемы**|Отображает дату и время последнего обновления метаданных для секции.|  
|**Название**|Отображает имя секции.|  
|**Режим обработки**|Выберите режим обработки для секции. Дополнительные сведения о режимах обработки для [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] объектов, см. в разделе [обработку объекта многомерных моделей](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).|  
|**Идентификатор удаленного источника данных**|Отображает идентификатор удаленного источника данных, из которого получают данные для секции.<br /><br /> Примечание. Это свойство содержит значение только для удаленных секций.|  
|**Срез**|Отображает выражение, которое определяет срез данных, представленных секцией.|  
|**Source**|Отображает таблицу или запрос, являющийся источником данных для секции.|  
|**Состояние**|Отображает текущее состояние обработки секции.|  
|**Место хранения**|Отображает папку, в которой хранятся данные для секции.<br /><br /> Примечание. Это свойство содержит значение только в том случае, если место хранения отличается от установленного по умолчанию для экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Тип**|Отображается тип секции.|  
  
## <a name="see-also"></a>См. также  
 [Секции &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Удаленные секции](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [Диалоговое окно свойств секции &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Выбор &#40;секционировать диалоговое окно свойств&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Упреждающее кэширование &#40;секционировать диалоговое окно свойств&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)   
 [Конфигурация ошибок при обработке измерения кубов, секции и &#40;службы SSAS — многомерные&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  

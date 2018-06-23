---
title: Назначение обработки секции | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b01498c14c460fe5566b14203bd8d70002f8f457
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189325"
---
# <a name="partition-processing-destination"></a>Назначение обработки секции
  Назначение обработки секций производит загрузку и обработку секции служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения о секциях см. в разделе [Секции (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md).  
  
 Назначение обработки секции имеет следующие характеристики:  
  
-   Параметры для выполнения добавочной обработки, полной обработки или обработки обновления.  
  
-   Возможность установки конфигурации ошибки для указания, будет ли обработка пропускать ошибки или произведет остановку обработки после указанного количества ошибок.  
  
-   Сопоставление входных столбцов и столбцов секционирования.  
  
 Дополнительные сведения об обработке объектов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
> [!NOTE]  
>  Описанные здесь задачи не применимы к табличным моделям служб Analysis Services.  Нельзя связать входные столбцы со столбцами секционирования для табличных моделей. Вместо этого для обработки секции следует использовать задачу выполнения DDL [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) служб Analysis Services.  
  
## <a name="configuration-of-the-partition-processing-destination"></a>Настройка назначения «Обработка секций»  
 Назначение обработки секций использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для соединения с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который содержит кубы и секции, обрабатываемые назначением. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Данное назначение имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор назначения обработки секций** , см. в следующих разделах:  
  
-   [Редактор назначения обработки секций &#40;страницы диспетчера соединений&#41;](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения обработки секций &#40;страница «сопоставления»&#41;](../partition-processing-destination-editor-mappings-page.md)  
  
-   [Редактор назначения обработки секций &#40;страница «Дополнительно»&#41;](../partition-processing-destination-editor-advanced-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Common Properties](../common-properties.md)  
  
-   [Пользовательские свойства назначения «Обработка секций»](partition-processing-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
  
---
title: "Назначение обработки секции | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.partitionprocessingdest.f1"
helpviewer_keywords: 
  - "секции [службы Analysis Services], обработка"
  - "назначение обработки секции [службы Integration Services]"
  - "назначения [службы Integration Services], обработка секции"
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# Назначение обработки секции
  Назначение обработки секций производит загрузку и обработку секции служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения о секциях см. в разделе [Секции (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md).  
  
 Назначение обработки секции имеет следующие характеристики:  
  
-   Параметры для выполнения добавочной обработки, полной обработки или обработки обновления.  
  
-   Возможность установки конфигурации ошибки для указания, будет ли обработка пропускать ошибки или произведет остановку обработки после указанного количества ошибок.  
  
-   Сопоставление входных столбцов и столбцов секционирования.  
  
 Дополнительные сведения об обработке объектов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
> [!NOTE]  
>  Описанные здесь задачи не применимы к табличным моделям служб Analysis Services.  Нельзя связать входные столбцы со столбцами секционирования для табличных моделей. Вместо этого для обработки секции следует использовать задачу выполнения DDL [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) служб Analysis Services.  
  
## Настройка назначения «Обработка секций»  
 Назначение обработки секций использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для соединения с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который содержит кубы и секции, обрабатываемые назначением. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Данное назначение имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор назначения обработки секций** , см. в следующих разделах:  
  
-   [Редактор назначения "Обработка секций" (страница "Диспетчер соединений")](../../integration-services/data-flow/partition-processing-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения "Обработка секций" (страница "Сопоставления")](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)  
  
-   [Редактор назначения "Обработка секций" (страница "Дополнительно")](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../Topic/Common%20Properties.md)  
  
-   [Пользовательские свойства назначения «Обработка секций»](../../integration-services/data-flow/partition-processing-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
---
title: "Назначение &#171;Обработка измерений&#187; | Microsoft Docs"
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
  - "sql13.dts.designer.dimensionprocessingdest.f1"
helpviewer_keywords: 
  - "назначение «Обработка измерений»"
  - "загрузка измерений"
  - "назначения [службы Integration Services], обработка измерения"
  - "измерения [службы Analysis Services], обработка"
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Назначение &#171;Обработка измерений&#187;
  Назначение «Обработка измерения» загружает и обрабатывает измерение служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения об измерениях см. в разделе [Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 Назначение «Обработка измерений» включает следующие элементы:  
  
-   Параметры для выполнения добавочной обработки, полной обработки или обработки обновления.  
  
-   Конфигурация ошибок, определяющая, пропускает ли ошибки обработка измерений или останавливается после определенного числа ошибок.  
  
-   Сопоставление входных столбцов со столбцами в таблицах измерения.  
  
 Дополнительные сведения об обработке объектов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Настройка назначения «Обработка измерения»  
 Назначение «Обработка измерений» использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , чтобы подключиться к проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащему измерения, обрабатываемые назначением. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md).  
  
 Данное назначение имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно настроить при помощи диалогового окна **Редактор назначения обработки измерений** , см. в одном из следующих разделов:  
  
-   [Редактор назначения "Обработка измерения" (страница "Диспетчер соединений")](../../integration-services/data-flow/dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения "Обработка измерения" (страница "Сопоставления")](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)  
  
-   [Редактор назначения "Обработка измерения" (страница "Дополнительно")](../../integration-services/data-flow/dimension-processing-destination-editor-advanced-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые можно задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующем разделе:  
  
-   [Общие свойства](../Topic/Common%20Properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## См. также  
 [Поток данных](../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
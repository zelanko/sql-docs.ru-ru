---
title: Назначение "Обработка измерений" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8ca91bb8788d44c8a5a51d84e3d56b7a2b05d95e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827361"
---
# <a name="dimension-processing-destination"></a>назначение «Обработка измерений»
  Назначение «Обработка измерения» загружает и обрабатывает измерение служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения об измерениях см. в разделе [Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 Назначение «Обработка измерений» включает следующие элементы:  
  
-   Параметры для выполнения добавочной обработки, полной обработки или обработки обновления.  
  
-   Конфигурация ошибок, определяющая, пропускает ли ошибки обработка измерений или останавливается после определенного числа ошибок.  
  
-   Сопоставление входных столбцов со столбцами в таблицах измерения.  
  
 Дополнительные сведения об обработке объектов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Настройка параметров обработки (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## <a name="configuration-of-the-dimension-processing-destination"></a>Настройка назначения «Обработка измерения»  
 Назначение «Обработка измерений» использует диспетчер соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , чтобы подключиться к проекту служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащему измерения, обрабатываемые назначением. Дополнительные сведения см. в статье [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).  
  
 Данное назначение имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно настроить при помощи диалогового окна **Редактор назначения обработки измерений** , см. в одном из следующих разделов:  
  
-   [Редактор назначения "Обработка измерения" (страница "Диспетчер соединений")](../dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения "Обработка измерения" (страница "Сопоставления")](../dimension-processing-destination-editor-mappings-page.md)  
  
-   [Редактор назначения "Обработка измерения" (страница "Дополнительно")](../dimension-processing-destination-editor-advanced-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые можно задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующем разделе:  
  
-   [Common Properties](../common-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Поток данных](data-flow.md)   
 [Преобразования служб Integration Services](transformations/integration-services-transformations.md)  
  
  

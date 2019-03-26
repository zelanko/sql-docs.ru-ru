---
title: Редактор назначения "SAP BW" (страница "Дополнительно") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwdestination.advanced.f1
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 627ce76e87807a54299c386afcf51486ca8f9309
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275172"
---
# <a name="sap-bw-destination-editor-advanced-page"></a>Редактор назначений SAP BW (страница «Дополнительно»)
  Используйте страницу **Дополнительно** **редактора назначений SAP BW**, чтобы задать дополнительные параметры, такие как размер пакета и сведения о времени ожидания.  
  
 Для получения дополнительных сведений о назначении SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Назначение SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие страницы «Дополнительно»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Дополнительно** , чтобы открыть страницу редактора **Дополнительно** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки назначения, может потребоваться связаться с администратором SAP.  
  
 **Размер пакета**  
 Укажите, сколько строк данных будут передаваться за один раз. Оптимальное значение для этого параметра зависит от системы SAP Netweaver BW и от возможной дополнительной обработки данных. Обычно значения от 2000 до 20 000 обеспечивают самую высокую производительность.  
  
 **Запустить цепочку процессов**  
 (Необязательно) Укажите имя цепочки процессов, которую нужно активировать после завершения загрузки данных.  
  
 **Время ожидания для InfoPackage**  
 Укажите максимальное число секунд, в течение которых назначение должно ожидать завершения InfoPackage.  
  
 **Дождаться завершения передачи данных**  
 Укажите, следует ли назначению ожидать завершения загрузки данных системой SAP Netweaver BW.  
  
 **Не запускать InfoPackage (только ожидание)**  
 Укажите, что назначение не инициирует включение InfoPackage, а ожидает уведомления о начале загрузки данных системой SAP Netweaver BW.  
  
## <a name="see-also"></a>См. также:  
 [Редактор назначений SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Редактор назначений SAP BW (страница "Сопоставления")](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Редактор назначений SAP BW (страница "Вывод ошибок")](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

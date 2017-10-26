---
title: "Редактор назначений SAP BW (страница «Вывод ошибок») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwdestination.erroroutput.f1
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f1b243b6fae68be78e20bbb87a18c16cb78d24f7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-destination-editor-error-output-page"></a>Редактор назначений SAP BW (страница «Вывод ошибок»)
  Используйте страницу **Вывод ошибок** диалогового окна **Редактор назначений SAP BW** для задания параметров обработки ошибок.  
  
 Для получения дополнительных сведений о назначении SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Назначение SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В окне **Редактор назначений SAP BW**щелкните **Вывод ошибок** , чтобы открыть страницу редактора **Вывод ошибок** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки назначения, может потребоваться связаться с администратором SAP.  
  
 **Вход или выход**  
 Просмотрите имя входных данных.  
  
 **Столбец**  
 Данный параметр не используется.  
  
 **Ошибка**  
 Задайте действие, которое необходимо выполнить в назначении при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Усечение**  
 Данный параметр не используется.  
  
 **Description**  
 Просмотрите описание операции.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действие, которое необходимо применить в назначении ко всем выбранным ячейкам при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## <a name="see-also"></a>См. также  
 [Редактор назначений SAP BW &#40; Страницы диспетчера соединений &#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Редактор назначений SAP BW &#40; Страница «сопоставления» &#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Редактор назначений SAP BW &#40; Страница "Дополнительно" &#41;](../../integration-services/data-flow/sap-bw-destination-editor-advanced-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  


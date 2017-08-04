---
title: "Редактор источников SAP BW (страница «Вывод ошибок») | Документы Microsoft"
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
- sql13.dts.designer.sapbwsource.erroroutput.f1
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 00e596fd1c4b200e4f0fe1342fa56a9a3191f991
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-source-editor-error-output-page"></a>Редактор источников SAP BW (страница «Вывод ошибок»)
  Используйте страницу **Вывод ошибок** **Редактора источников SAP BW** для выбора параметров обработки ошибок и задания свойств выходных столбцов ошибок.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В окне **Редактор источников SAP BW**щелкните **Вывод ошибок** , чтобы открыть страницу редактора **Вывод ошибок** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки источника, может потребоваться связаться с администратором SAP.  
  
 **Вход или выход**  
 Просмотр имени источника данных.  
  
 **Столбец**  
 Просмотрите внешние (исходные) столбцы, выбранные на странице **Столбцы** диалогового окна **Редактор источников SAP BW** . Дополнительные сведения об этом диалоговом окне см. в разделе [Редактор источника SAP BW (страница "Столбцы")](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md).  
  
 **Ошибка**  
 Укажите действия компонента источника SAP BW при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Усечение**  
 Укажите действия компонента источника SAP BW при выполнении усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Description**  
 Просмотреть описание ошибки.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действия для компонента источника SAP BW, которые необходимо выполнить со всеми выбранными ячейками при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Редактор источников SAP BW &#40; Страница «столбцы» &#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Редактор источников SAP BW &#40; Страница "Дополнительно" &#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

---
title: "Редактор источника SAP BW (страница \"Столбцы\") | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.sapbwsource.columns.f1
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c6bb6d1d1061314752207fce3cdb5123daa57104
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sap-bw-source-editor-columns-page"></a>Редактор источников SAP BW (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор источников SAP BW** используется для сопоставления выходного столбца с каждым внешним (исходным) столбцом.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие страницы «Столбцы»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В **Редакторе источников SAP BW**щелкните **Столбцы** , чтобы открыть страницу редактора **Столбцы** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки источника, может потребоваться связаться с администратором SAP.  
  
 **Доступные внешние столбцы**  
 Просмотрите список доступных внешних столбцов в источнике данных, а затем выберите столбцы, которые нужно включить в поток данных.  
  
 Чтобы включить столбец в поток данных, установите флажок, соответствующий этому столбцу. Порядок, в котором устанавливаются флажки, определяет порядок вывода столбцов. Таким образом, первый установленный флажок будет указывать первый выводимый столбец, второй флажок будет указывать второй выводимый столбец и т. д.  
  
 **Внешний столбец**  
 Просмотрите выбранные внешние (исходные) столбцы. Выбранные столбцы отобразятся в том порядке, в котором будут отображаться соответствующие выводимые столбцы при настройке компонентов нисходящего потока, использующих данные из этого источника.  
  
 Для изменения порядка столбцов в списке **Доступные внешние столбцы** снимите флажки для всех столбцов. После этого выберите столбцы в том порядке, в котором они должны отображаться.  
  
 **Выходной столбец**  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца. Однако можно ввести любое уникальное описательное имя. [!INCLUDE[ssIS](../../includes/ssis-md.md)] отобразятся имена **Выходной столбец** при настройке компонентов нисходящего потока, использующих данные из этого источника.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Редактор источника SAP BW (страница "Вывод ошибок")](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [Редактор источника SAP BW (страница "Дополнительно")](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

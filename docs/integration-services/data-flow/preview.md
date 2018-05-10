---
title: Предварительный просмотр | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 30b7a2f84933fba99cc0497b18de1e07e69ea77f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="preview"></a>Предварительный просмотр
  В диалоговом окне **Предварительный просмотр** можно просмотреть данные, извлекаемые источником SAP BW.  
  
> [!IMPORTANT]  
>  Параметр **Предварительный просмотр** , доступный на странице **Диспетчер соединений** **Редактора источника SAP BW**, непосредственно извлекает данные. Если настроить SAP Netweaver BW для извлечения только тех данных, которые изменились со времени предыдущего сеанса извлечения, то при выборе параметра **Предварительный просмотр** просматриваемые данные будут исключены из следующего сеанса извлечения.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие диалогового окна «Предварительный просмотр»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В **Редакторе источника SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  Настройте источник SAP BW.  
  
5.  После настройки источника SAP BW на странице **Диспетчер соединений** щелкните **Предварительный просмотр** для предварительного просмотра данных в диалоговом окне **Предварительный просмотр** .  
  
    > [!NOTE]  
    >  При щелчке **Предварительный просмотр** также открывается диалоговое окно **Журнал запросов** . Дополнительные сведения об этом диалоговом окне см. в разделе [Request Log](../../integration-services/data-flow/request-log.md).  
  
## <a name="options"></a>Параметры  
 В диалоговом окне **Предварительный просмотр** отображаются строки, запрошенные в системе SAP Netweaver BW. Отображаемые столбцы — это столбцы, определенные в исходных данных.  
  
 В этом диалоговом окне отсутствуют другие параметры.  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

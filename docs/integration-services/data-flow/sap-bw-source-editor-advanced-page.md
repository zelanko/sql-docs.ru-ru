---
title: Редактор источника SAP BW (страница "Дополнительно") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwsource.advanced.f1
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4111e6f64030d16da75c52ed60b6d0744b3fb58f
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65726412"
---
# <a name="sap-bw-source-editor-advanced-page"></a>Редактор источников SAP BW (страница «Дополнительно»)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Используйте страницу **Дополнительно** **Редактора источников SAP BW** , чтобы указать правило преобразования строк и время ожидания, а также сбросить состояние запроса с определенным идентификатором.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие страницы «Диспетчер соединений»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В **Редакторе источников SAP BW**щелкните **Дополнительно** , чтобы открыть страницу редактора **Дополнительно** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки источника, может потребоваться связаться с администратором SAP.  
  
 **Преобразование строк**  
 Укажите правило для преобразования строк.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Автоматическое преобразование строк**|Преобразовать все строки в **nvarchar** , если система SAP Netweaver BW поддерживает Юникод. В противном случае все строки преобразуются в **varchar**.|  
|**Преобразование строк в varchar**|Все строки преобразуются в **varchar**.|  
|**Преобразование строк в nvarchar**|Все строки преобразуются в **nvarchar**.|  
  
 **Время ожидания (в секундах)**  
 Укажите максимальное число секунд для периода ожидания источника.  
  
> [!NOTE]  
>  Этот параметр допустим только в том случае, если выбран параметр **W — ждать уведомления** в качестве значения **Режим выполнения** на странице редактора **Диспетчер соединений** . Дополнительные сведения см. в разделе [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md).  
  
 **Идентификатор запроса**  
 Укажите идентификатор запроса, состояние которого необходимо сбрасывать до "G — зеленый" при нажатии кнопки **Сброс**.  
  
 **Сброс**  
 Позволяет сбросить состояние идентификатора запроса до «G — зеленый», после отображения запроса на подтверждение. Это может быть полезным, если произошла ошибка и система SAP Netweaver BW отметила запрос с состоянием «Красный» или «Желтый».  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Редактор источника SAP BW (страница "Столбцы")](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Редактор источника SAP BW (страница "Вывод ошибок")](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

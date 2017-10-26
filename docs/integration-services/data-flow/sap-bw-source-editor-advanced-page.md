---
title: "Редактор источников SAP BW (страница «Дополнительно») | Документы Microsoft"
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
- sql13.dts.designer.sapbwsource.advanced.f1
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ac7757987c169f803f3b0adda7f27c94f090d7db
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-source-editor-advanced-page"></a>Редактор источников SAP BW (страница «Дополнительно»)
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
  
|Параметр|Description|  
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
  
## <a name="see-also"></a>См. также  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Редактор источников SAP BW &#40; Страница «столбцы» &#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Редактор источников SAP BW &#40; Страница «Вывод ошибок» &#41;](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  


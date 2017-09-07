---
title: "Редактор назначений SAP BW (страница «Диспетчер соединений») | Документы Microsoft"
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
- sql13.dts.designer.sapbwdestination.connection.f1
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 17d5ce8dd762a61b6dcbf4f2363d78c090495690
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-destination-editor-connection-manager-page"></a>Редактор назначений SAP BW (страница «Диспетчер соединений»)
  Используйте страницу **Диспетчер соединений** диалогового окна **Редактор назначений SAP BW** для выбора диспетчера соединений SAP BW, который будет использоваться назначением SAP BW. На этой странице можно также выбрать параметры для загрузки данных в систему SAP Netweaver BW.  
  
 Для получения дополнительных сведений о назначении SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Назначение SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие страницы «Диспетчер соединений»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки назначения, может потребоваться связаться с администратором SAP.  
  
 **Диспетчер соединений SAP BW**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер соединений с помощью диалогового окна **Диспетчер соединений SAP BW** .  
  
 **Пробная нагрузка**  
 Выполните тест процесса загрузки, в которой используются выбранные параметры и не загружается ни одной строки.  
  
### <a name="infopackageinfosource-options"></a>Параметры InfoPackage/InfoSource  
 Нет необходимости в изучении или вводе этих значений заранее. Нажмите кнопку **Поиск** , чтобы найти и выбрать соответствующий InfoPackage. После выбора InfoPackage компонент вводит соответствующие значения для этих параметров.  
  
 **InfoPackage**  
 Введите имя InfoPackage.  
  
 **InfoSource**  
 Введите имя InfoSource.  
  
 **Тип**  
 Введите один символ, который определяет тип InfoSource. В следующей таблице перечислены допустимые значения, состоящие из одного символа.  
  
|Значение|Description|  
|-----------|-----------------|  
|**D**|Данные транзакций|  
|**M**|Основные данные|  
|**T**|Тексты|  
|**З**|Данные иерархии|  
  
 **Логическая система**  
 Введите имя логической системы, связанной с InfoPackage.  
  
 **Поиск**  
 Выполните поиск InfoPackage с помощью диалогового окна **Поиск InfoPackage** . Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up InfoPackage](../../integration-services/data-flow/look-up-infopackage.md).  
  
### <a name="rfc-destination-options"></a>Параметры назначения RFC  
 Нет необходимости в изучении или вводе этих значений заранее. Нажмите кнопку **Поиск** , чтобы найти и выбрать соответствующее назначение RFC. После выбора назначения RFC компонент вводит соответствующие значения для этих параметров.  
  
 **Узел шлюза**  
 Введите имя или IP-адрес сервера узла шлюза. Обычно имя или IP-адрес совпадают с аналогичными данными сервера приложений SAP.  
  
 **Служба шлюза**  
 Введите имя службы шлюза в формате **sapgwNN**, где **NN** — номер системы.  
  
 **ID программы**  
 Введите идентификатор программы, связанный с назначением RFC.  
  
 **Поиск**  
 Выполните поиск назначения RFC с помощью диалогового окна **Поиск назначения RFC** . Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up RFC Destination](../../integration-services/data-flow/look-up-rfc-destination.md).  
  
### <a name="create-sap-bw-objects-options"></a>Параметры создания объектов SAP BW  
 **Выбрать тип объекта**  
 Выберите тип объекта SAP Netweaver BW, который нужно создать. Можно выбрать один из следующих типов.  
  
-   InfoObject  
  
-   InfoCube  
  
-   InfoSource  
  
-   InfoPackage  
  
 **Создание**  
 Создается выбранный тип объекта SAP Netweaver BW.  
  
|Тип объекта|Результат|  
|-----------------|------------|  
|**InfoObject**|Создается новый InfoObject с помощью диалогового окна **Создание нового InfoObject** . Дополнительные сведения об этом диалоговом окне см. в разделе [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).|  
|**InfoCube**|Создается новый InfoCube с помощью диалогового окна **Создание InfoCube для данных транзакции** . Дополнительные сведения об этом диалоговом окне см. в разделе [Create InfoCube for Transaction Data](../../integration-services/data-flow/create-infocube-for-transaction-data.md).|  
|**InfoSource**|Создайте новый InfoSource с помощью диалогового окна **Создание InfoSource** , а затем используйте для этого диалоговое окно **Создание InfoSource для данных транзакции** или **Создание InfoSource для основных данных** . Дополнительные сведения об этих диалоговых окнах см. в разделах [Create InfoSource](../../integration-services/data-flow/create-infosource.md), [Create InfoSource for Transaction Data](../../integration-services/data-flow/create-infosource-for-transaction-data.md) и [Create InfoSource for Master Data](../../integration-services/data-flow/create-infosource-for-master-data.md).|  
|**InfoPackage**|Создайте новый InfoPackage, используя диалоговое окно **Создание InfoPackage** . Дополнительные сведения об этом диалоговом окне см. в разделе [Create InfoPackage](../../integration-services/data-flow/create-infopackage.md).|  
  
## <a name="see-also"></a>См. также  
 [Редактор назначений SAP BW &#40; Страница «сопоставления» &#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Редактор назначений SAP BW &#40; Страница «Вывод ошибок» &#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [Редактор назначений SAP BW &#40; Страница "Дополнительно" &#41;](../../integration-services/data-flow/sap-bw-destination-editor-advanced-page.md)   
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

---
title: Поиск назначения RFC | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 968511e873af77e0f8d36cfc0d8b8eba73020653
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400436"
---
# <a name="look-up-rfc-destination"></a>Поиск назначения RFC
  Используйте диалоговое окно **Поиск назначения RFC** для поиска назначения RFC, определенного в системе SAP Netweaver BW. После открытия списка доступных назначений RFC выберите необходимое назначение и компонент заполнит связанные параметры необходимыми значениями.  
  
 Источник и назначение SAP BW используют диалоговое окно **Поиск назначения RFC** . Дополнительные сведения об этих компонентах [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. в разделах [Источник SAP BW](../../integration-services/data-flow/sap-bw-source.md) и [Назначение SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окно «Поиск назначения RFC»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник или назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник или назначение SAP BW.  
  
3.  В **Редактор источников SAP BW** или **Редактор назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На странице **Диспетчер соединений** в поле группы **Назначение RFC** щелкните **Поиск** , чтобы открыть диалоговое окно **Поиск назначения RFC** .  
  
     На вкладке **Редактор источников SAP BW**поле группы **Назначение RFC** отображается только в случае, если параметр **Режим выполнения** имеет значение **P — запустить цепочку процесса** или **W — ждать уведомления**.  
  
## <a name="options"></a>Параметры  
 **Назначение**  
 Просмотрите имя назначения RFC, определенное в системе SAP Netweaver BW.  
  
 **Узел шлюза**  
 Просмотрите имя или IP-адрес сервера узла шлюза. Обычно имя или IP-адрес совпадают с аналогичными данными сервера приложений SAP.  
  
 **Служба шлюза**  
 Просмотрите имя службы шлюза в формате **sapgwNN**, где **NN** — номер системы.  
  
 **ID программы**  
 Просмотрите идентификатор программы, связанный с назначением RFC.  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Редактор назначений SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

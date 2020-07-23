---
title: Соединитель Microsoft Connector для SAP BW | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12375a5d09c34ac9b9e79e99efdee3ccebbe823b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918115"
---
# <a name="microsoft-connector-for-sap-bw"></a>Соединитель Microsoft Connector для SAP BW

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW состоит из трех компонентов, позволяющих извлекать данные из системы SAP Netweaver BW версии 7 и загружать их в нее.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW для SQL Server 2016 входит в пакет дополнительных компонентов SQL Server 2016. Чтобы установить Connector для SAP BW и сопутствующую документацию, скачайте и запустите установщик [с веб-страницы пакета дополнительных компонентов SQL Server 2016](https://go.microsoft.com/fwlink/?LinkId=746297).  

> [!IMPORTANT]
> Корпорация Майкрософт не планирует предоставлять обновленные версии соединителя для SAP BW. Майкрософт не владеет исходным кодом компонентов SAP BW сторонних разработчиков и не может их обновлять. Вы можете приобрести новейшие компоненты подключения SAP у независимого поставщика программного обеспечения, который является партнером Майкрософт, например у [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html). Независимые поставщики программного обеспечения, являющиеся партнерами Майкрософт, адаптировали свои компоненты подключений SAP под SSIS для установки в Azure.
 
> [!IMPORTANT]  
>  Для работы с документацией по Microsoft Connector для SAP BW вы должны иметь представление о среде SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
## <a name="components"></a>Components  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW состоит из следующих компонентов:  
  
-   **SAP BW Source** — это компонент потока данных, который позволяет извлекать данные из системы SAP Netweaver BW версии 7.  
  
-   **SAP BW Destination** — это компонент потока данных, позволяющий загружать данные в систему SAP Netweaver BW версии 7.  
  
-   **Диспетчер соединений SAP BW** подключает источник SAP BW или назначение SAP BW к системе SAP Netweaver BW версии 7.  
  
 Пошаговое руководство, в котором показано, как настроить и использовать диспетчер соединений, источник и назначение SAP BW см. в техническом документе [Использование службы SQL Server Integration Services с SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897). В этом техническом документе также показано, как настроить необходимые объекты в SAP BW.  
  
## <a name="documentation"></a>Документация  
 Файл справки по [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW содержит следующие разделы и подразделы:  
  
 [Установка Microsoft Connector для SAP BW](../integration-services/installing-the-microsoft-connector-for-sap-bw.md)  
 Описывает требования к установке [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW.  
  
 [Компоненты Microsoft Connector для SAP BW](../integration-services/microsoft-connector-for-sap-bw-components.md)  
 Описывает каждый компонент [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW.  
  
 [Справка F1 по Microsoft Connector для SAP BW](../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
 Описывает пользовательский интерфейс каждого компонента [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW.  
  
  

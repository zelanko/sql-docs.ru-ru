---
title: "Создать InfoPackage | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e893ddd6b0461a3f6b3e20146a79e63c7fcc1c4
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-infopackage"></a>Создать InfoPackage
  Используйте диалоговое окно **Создать InfoPackage** для создания нового InfoPackage в системе SAP Netweaver BW.  
  
 Диалоговое окно **Создать InfoPackage** можно открыть на странице **Диспетчер соединений** **Редактора назначений SAP BW**. Дополнительные сведения о назначении SAP BW см. в статье [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Создание InfoPackage»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На вкладке **Диспетчер соединений** в поле группы **Создание объектов SAP BW** выберите **InfoPackage**и щелкните **Создать**.  
  
## <a name="options"></a>Параметры  
 **InfoSource**  
 Введите имя InfoSource, на основе которого должен быть создан новый InfoPackage.  
  
 **Краткое описание**  
 Введите описание нового InfoPackage.  
  
 **Исходная система**  
 Выберите исходную систему, с которой должен быть связан новый InfoPackage.  
  
 **Атрибуты**  
 Указывает, что InfoPackage загрузит данные атрибутов.  
  
 **Тексты**  
 Указывает, что InfoPackage загрузит текстовые данные.  
  
 **Transaction**  
 Указывает, что InfoPackage загрузит данные транзакций.  
  
 **Сохранить и активировать**  
 Сохраните и включите новый InfoPackage.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по Microsoft Connector для SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

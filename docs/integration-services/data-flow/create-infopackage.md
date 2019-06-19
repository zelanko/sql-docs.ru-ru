---
title: Создать InfoPackage | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ec8b4ee24e4217492c34319f94976aed44550037
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727082"
---
# <a name="create-infopackage"></a>Создать InfoPackage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  

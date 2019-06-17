---
title: Создание InfoSource для основных данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b52a9a89-8380-4a02-8a83-dcfb46ae860e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 87ada4ef6cf9266720ac0c9742440d0d60345c88
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62827957"
---
# <a name="create-infosource-for-master-data"></a>Создание InfoSource для основных данных
  Используйте диалоговое окно **Создание InfoSource для основных данных** для создания нового InfoSource для основных данных в системе SAP Netweaver BW.  
  
 Диалоговое окно **Создание InfoSource для основных данных** можно открыть на странице **Диспетчер соединений** **Редактора назначений SAP BW**. Дополнительные сведения о назначении SAP BW см. в статье [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Создание InfoSource для основных данных»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На вкладке **Диспетчер соединений** в поле группы **Создание объектов SAP BW** выберите **InfoSource**и щелкните **Создать**.  
  
5.  В диалоговом окне **Создание InfoSource** выберите **Основные данные**и нажмите кнопку **ОК**.  
  
## <a name="options"></a>Параметры  
 **Имя InfoObject**  
 Введите имя InfoObject, на основе которого должен быть создан новый InfoSource.  
  
 **Поиск**  
 Поиск InfoObject. Этот параметр открывает диалоговое окно **Поиск InfoObject** , в котором можно выбрать InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up InfoObject](look-up-infoobject.md).  
  
 После выбора InfoObject компонент указывает в текстовом поле **Имя InfoObject** имя выбранного InfoObject.  
  
 **Создать**  
 Создание нового InfoObject Этот параметр открывает диалоговое окно **Создание InfoObject**, в котором можно создать InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Create New InfoObject](create-new-infoobject.md).  
  
 После создания InfoObject компонент указывает в текстовом поле **Имя InfoObject** имя нового InfoObject.  
  
 **Краткое описание**  
 Введите краткое описание нового InfoSource.  
  
 **Полное описание**  
 Введите полное описание нового InfoSource.  
  
 **Исходная система**  
 Выберите исходную систему, которая будет связана с новым InfoSource.  
  
 **Приложение**  
 Введите имя приложения, которое необходимо связать с новым InfoSource.  
  
 **Атрибуты**  
 Указывает, что основные данные состоят из атрибутов.  
  
 **Тексты**  
 Указывает, что основные данные состоят из атрибутов.  
  
 **Сохранить и активировать**  
 Сохраните и активируйте новый InfoSource.  
  
## <a name="see-also"></a>См. также  
 [Создание InfoSource](create-infosource.md)   
 [Справка F1 по Microsoft Connector 1.1 для SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  

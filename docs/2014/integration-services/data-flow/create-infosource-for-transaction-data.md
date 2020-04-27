---
title: Создание InfoSource для данных транзакции | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6d99a357c754add722fb6d5b5d880d1c472a5989
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62827937"
---
# <a name="create-infosource-for-transaction-data"></a>Создание InfoSource для данных транзакции
  Используйте диалоговое окно **Создание InfoSource для данных транзакции** , чтобы создать новый InfoSource для данных транзакции в системе SAP Netweaver BW.  
  
 Можно открыть диалоговое окно **Создание InfoSource для данных транзакции** на странице **Диспетчер соединений** **Редактора назначений SAP BW**. Дополнительные сведения о назначении SAP BW см. в статье [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Создание InfoSource для данных транзакции»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На вкладке **Диспетчер соединений** в поле группы **Создание объектов SAP BW** выберите **InfoSource**и щелкните **Создать**.  
  
5.  В диалоговом окне **Создание InfoSource** выберите **Данные транзакции**и нажмите кнопку **ОК**.  
  
## <a name="general-options"></a>Общие параметры  
 **Имя InfoSource**  
 Введите имя нового InfoSource.  
  
 **Краткое описание**  
 Введите краткое описание нового InfoSource.  
  
 **Полное описание**  
 Введите полное описание нового InfoSource.  
  
 **Исходная система**  
 Выберите исходную систему, связанную с InfoSource.  
  
 **Сохранить и активировать**  
 Сохраните и активируйте новый InfoSource.  
  
## <a name="infosource-transfer-structure-options"></a>Параметры переноса структуры InfoSource  
 Средство переноса InfoSource позволяет сопоставить столбцы потока данных и источники InfoSource.  
  
 **PipelineElement**  
 Отображает столбец среди выходных данных потока, подключенного к целевому месту SAP BW.  
  
 **PipelineDataType**  
 Отображает тип данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для столбца потока данных.  
  
 **Iobject — поиск**  
 Сопоставьте существующий InfoObject со столбцом потока данных для текущей строки. Чтобы создать это сопоставление, щелкните **Найти**, а затем используйте диалоговое окно **Поиск InfoObject** для выбора существующего InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up InfoObject](look-up-infoobject.md).  
  
 После выбора существующего InfoObject компонент заполняет столбцы **InfoObject** и **Тип** выбранными значениями.  
  
 **Iobject — создать**  
 Создайте новый InfoObject и свяжите этот новый InfoObject со столбцом потока данных в текущей строке. Для создания нового InfoObject щелкните **Создать**, а затем используйте диалоговое окно **Создание InfoObject** для создания InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Create New InfoObject](create-new-infoobject.md).  
  
 После создания нового InfoObject компонент заполняет столбцы **InfoObject** и **Тип** новыми значениями.  
  
 **Iobject — удаление**  
 Удаляет взаимосвязь между InfoObject и столбцом потока данных для текущей строки. Чтобы удалить эту связь, нажмите кнопку **Удалить**.  
  
 **InfoObject**  
 Отображает имя InfoObject, связанное со столбцом потока данных.  
  
 **Тип**  
 Отображает тип InfoObject, связанный со столбцом потока данных. В следующей таблице приводятся возможные значения типа.  
  
|Значение|Description|  
|-----------|-----------------|  
|CHA|Характеристики|  
|UNI|Units|  
|KYF|Ключевые цифры|  
|TIM|Характеристики времени|  
  
 **Поле единицы**  
 Укажите единицы, которые будут использоваться в InfoObject.  
  
## <a name="see-also"></a>См. также:  
 [Создание InfoSource](create-infosource.md)   
 [Справка F1 по Microsoft Connector 1.1 для SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  

---
title: "Поиск InfoPackage | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b576561f0d49a6a3008fe59176fe2ec2c1368fa3
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="look-up-infopackage"></a>Поиск InfoPackage
  Используйте диалоговое окно **Поиск InfoPackage** для поиска InfoPackage, определенного в системе SAP Netweaver BW. После открытия списка InfoPackage выберите необходимый InfoPackage, и назначение заполнит связанные параметры необходимыми значениями.  
  
 Назначение SAP BW [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW использует диалоговое окно **Поиск цепочки процессов** . Дополнительные сведения о назначении SAP BW см. в разделе [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Поиск InfoPackage»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На странице **Диспетчер соединений** в поле группы **InfoPackage/InfoSource** щелкните **Поиск** , чтобы открыть диалоговое окно **Поиск InfoPackage** .  
  
## <a name="lookup-options"></a>Параметры поиска  
 В полях поиска можно фильтровать результаты с помощью символа-шаблона звездочки (*) или с помощью частичной строки в сочетании с символом-шаблоном звездочки. Однако если оставить поле поиска пустым, то критериям поиска в этом поле будут соответствовать только пустые строки.  
  
 **InfoPackage**  
 Введите для поиска имя или часть имени InfoPackage с символом-шаблоном звездочки (*). Также можно использовать символ-шаблон звездочки для включения всех InfoPackage.  
  
 **InfoSource**  
 Введите имя или часть имени InfoSource с символом-шаблоном звездочки (*). Также можно использовать символ-шаблон звездочки для включения всех InfoPackage независимо от InfoSource.  
  
 **Исходная система**  
 Введите имя или часть имени исходной системы с символом-шаблоном звездочки (*). Также можно использовать символ-шаблон звездочки для включения всех InfoPackage независимо от исходных систем.  
  
 **Найти**  
 Выполните поиск соответствующих InfoPackage, определенных в системе SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Результаты поиска  
 После нажатия кнопки «Поиск» список InfoPackage в системе SAP Netweaver BW отобразится в таблице со следующими заголовками столбцов.  
  
 **InfoPackage**  
 Отображается имя InfoPackage, определенное в системе SAP Netweaver BW.  
  
 **Тип**  
 Отображается тип InfoPackage. В следующей таблице приводятся возможные значения типа.  
  
|Значение|Description|  
|-----------|-----------------|  
|транзакций|Данные транзакций.|  
|Аттр.|Данные атрибутов.|  
|Тексты|Тексты.|  
  
 **Описание**  
 Отображается описание InfoPackage.  
  
 **InfoSource**  
 Отображается имя InfoSource (если существует), которое связано с InfoPackage.  
  
 **Source System**  
 Отображается имя исходной системы.  
  
 После открытия списка InfoPackage выберите необходимый InfoPackage, и назначение заполнит связанные параметры необходимыми значениями.  
  
## <a name="see-also"></a>См. также:  
 [Редактор назначений SAP BW (страница "Диспетчер подключений")](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Справка F1 по соединителю с SAP BW (Microsoft)](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

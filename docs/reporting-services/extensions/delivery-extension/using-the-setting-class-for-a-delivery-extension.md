---
title: "Использование класса Setting для модуля доставки | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
caps.latest.revision: "32"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9fc8237685799035d5eae1448bd1d71ab18f5016
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Использование класса Setting для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> находится в пространстве имен <xref:Microsoft.ReportingServices.Interfaces> и представляет сведения о параметрах настройки для модуля доставки. Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> предусматривает инфраструктуру для хранения информации о параметрах, необходимых для нормального функционирования модуля доставки. Так, в модуле доставки электронной почты сервера отчетов необходимо указывать параметры, требуемые для доставки электронной почты, такие как адрес получателя, адрес отправителя, строка темы электронного письма и т.д. Разумеется, для того, чтобы модуль доставки мог доставлять уведомления и отчеты, нестандартные поставщики доставки будут требовать от пользователя указания соответствующих параметров.  
  
 Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> используется при реализации свойства <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> интерфейса <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. Кроме того, класс <xref:Microsoft.ReportingServices.Interfaces.Setting> используется для обработки данных настройки модуля, предоставляемых пользователем при создании подписки или уведомления.  
  
 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.Setting> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

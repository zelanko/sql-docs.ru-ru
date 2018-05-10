---
title: Использование класса Setting для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5d74af9c4f9c1b5f9ddfd1504ad200f5d6ffa49b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Использование класса Setting для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> находится в пространстве имен <xref:Microsoft.ReportingServices.Interfaces> и представляет сведения о параметрах настройки для модуля доставки. Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> предусматривает инфраструктуру для хранения информации о параметрах, необходимых для нормального функционирования модуля доставки. Так, в модуле доставки электронной почты сервера отчетов необходимо указывать параметры, требуемые для доставки электронной почты, такие как адрес получателя, адрес отправителя, строка темы электронного письма и т.д. Разумеется, для того, чтобы модуль доставки мог доставлять уведомления и отчеты, нестандартные поставщики доставки будут требовать от пользователя указания соответствующих параметров.  
  
 Класс <xref:Microsoft.ReportingServices.Interfaces.Setting> используется при реализации свойства <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> интерфейса <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. Кроме того, класс <xref:Microsoft.ReportingServices.Interfaces.Setting> используется для обработки данных настройки модуля, предоставляемых пользователем при создании подписки или уведомления.  
  
 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.Setting> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

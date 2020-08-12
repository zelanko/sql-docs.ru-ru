---
title: Реализация модуля доставки | Документы Майкрософт
description: Ознакомьтесь с обзором того, как можно расширить функциональные возможности доставки в Reporting Services путем реализации пользовательского модуля доставки.
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d0ac797a8dd02a9d854c8bb2783435a087326f48
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529571"
---
# <a name="implementing-a-delivery-extension"></a>Реализация модуля доставки
  С помощью среды [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] пользователи могут создавать и публиковать отчеты, которые затем можно доставлять в различные места. Кроме того, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] содержат несколько модулей доставки и API-интерфейс доставки, который позволяет разработчикам создавать дополнительные модули доставки, расширяя возможности доставки в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Образец реализации модуля доставки см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях доставки](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 Введение в процесс написания пользовательского модуля доставки для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Подготовка к реализации модуля доставки](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 Описывает интерфейсы и классы, доступные при реализации модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также вопросы, которые следует обдумать перед реализацией.  
  
 [Создание библиотеки модулей доставки](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 Описывается процесс присвоения пространства имен модулю доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и процесс компиляции модуля доставки в DLL-библиотеку.  
  
 [Реализация интерфейса IDeliveryExtension для модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Описывает атрибуты модуля доставки и процесс реализации собственного класса модуля доставки.  
  
 [Использование класса Notification для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Notification** и способ его использования в реализации модуля доставки.  
  
 [Использование класса Setting для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Setting** и способ его использования в реализации модуля доставки.  
  
 [Использование класса Report для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **Report** и способ его использования в реализации модуля доставки.  
  
 [Использование класса RenderedOutputFile для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Описывает атрибуты класса **RenderedOutputFile** и способ его использования в реализации модуля доставки.  
  
 [Развертывание модуля доставки](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 Описывается процесс развертывания модуля доставки.  
  
 [Отладка кода модулей доставки](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 Описывается процесс отладки кода модулей доставки.  
  
 [Удаление модуля доставки](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 Описывается процесс удаления модуля доставки с сервера отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

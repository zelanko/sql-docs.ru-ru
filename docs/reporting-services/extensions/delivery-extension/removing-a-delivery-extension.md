---
title: "Удаление модуля доставки | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
caps.latest.revision: "31"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 659c572c6f9a2b013e3ae3f182418bacc0f89b50
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="removing-a-delivery-extension"></a>Удаление модуля доставки
  Чтобы удалить модуль доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], нужно просто удалить элемент **Extension** для модуля доставки из файла конфигурации. После удаления сведений конфигурации модуль доставки перестает быть доступным для сервера отчетов.  
  
 После удаления соответствующего модулю доставки элемента **Extension** из файла конфигурации для этого модуля отменяется регистрация на сервере отчетов. Сервер отчетов удаляет запись из списка модулей доставки и отменяет активацию подписок, использующих этот модуль доставки. После удаления модуля доставки пользователи не смогут выбрать его в качестве метода уведомления.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

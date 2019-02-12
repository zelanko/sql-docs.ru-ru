---
title: Удаление модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5efe51d0c91a0321a17e539aeddbb26f0dc3a5fe
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036260"
---
# <a name="removing-a-delivery-extension"></a>Удаление модуля доставки
  Чтобы удалить модуль доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], нужно просто удалить элемент **Extension** для модуля доставки из файла конфигурации. После удаления сведений конфигурации модуль доставки перестает быть доступным для сервера отчетов.  
  
 После удаления соответствующего модулю доставки элемента **Extension** из файла конфигурации для этого модуля отменяется регистрация на сервере отчетов. Сервер отчетов удаляет запись из списка модулей доставки и отменяет активацию подписок, использующих этот модуль доставки. После удаления модуля доставки пользователи не смогут выбрать его в качестве метода уведомления.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  

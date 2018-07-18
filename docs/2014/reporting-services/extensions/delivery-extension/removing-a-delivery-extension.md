---
title: Удаление модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b216e2c711b2a51b0e43438f804902185a9c098c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253456"
---
# <a name="removing-a-delivery-extension"></a>Удаление модуля доставки
  Чтобы удалить модуль доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], нужно просто удалить элемент **Extension** для модуля доставки из файла конфигурации. После удаления сведений конфигурации модуль доставки перестает быть доступным для сервера отчетов.  
  
 После удаления соответствующего модулю доставки элемента **Extension** из файла конфигурации для этого модуля отменяется регистрация на сервере отчетов. Сервер отчетов удаляет запись из списка модулей доставки и отменяет активацию подписок, использующих этот модуль доставки. После удаления модуля доставки пользователи не смогут выбрать его в качестве метода уведомления.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  

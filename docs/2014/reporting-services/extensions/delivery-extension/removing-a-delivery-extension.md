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
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 249d54aba50465d7732595d2c8e3c90a2de0225f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193533"
---
# <a name="removing-a-delivery-extension"></a>Удаление модуля доставки
  Чтобы удалить модуль доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], нужно просто удалить элемент **Extension** для модуля доставки из файла конфигурации. После удаления сведений конфигурации модуль доставки перестает быть доступным для сервера отчетов.  
  
 После удаления соответствующего модулю доставки элемента **Extension** из файла конфигурации для этого модуля отменяется регистрация на сервере отчетов. Сервер отчетов удаляет запись из списка модулей доставки и отменяет активацию подписок, использующих этот модуль доставки. После удаления модуля доставки пользователи не смогут выбрать его в качестве метода уведомления.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
---
title: Поставщик инструментария WMI для управления конфигурации
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 21ca5f7039b11b30c11a0fb707f6b6e89244bae2
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658916"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Основные сведения о поставщике WMI для управления конфигурацией
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет поставщик WMI для управления конфигурацией. Это позволяет использовать инструментарий управления Windows для управления службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сетевыми параметрами сервера и его псевдонимами. службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сетевые параметры и псевдонимы представлены объектами WMI в пространстве имен Рут\микрософт\склсервер\компутерманажемент*nn* компьютера. После установления соединения с поставщиком WMI на некотором компьютере службы сетевые параметры и псевдонимы можно запрашивать с помощью WQL или языка сценариев.  
  
 Поставщик WMI является поставщиком экземпляров. Он предоставляет экземпляры [классов WMI](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) и поддерживает следующие асинхронные операции.  
  
 Получение экземпляра  
 Получение экземпляра определенного типа класса.  
  
 Перечисление  
 Перечисление всех экземпляров типа класса.  
  
 Изменение  
 Изменение определенного экземпляра типа класса.  
  
 Классы содержат методы, позволяющие изменять их свойства.  
  
 Удаление  
 Удаление определенного экземпляра типа класса.  
  
 Обработка запросов  
 Перечисление экземпляров типа класса на основе фильтра.  
  
 Примеры приложения управления с помощью поставщика WMI для управления конфигурацией см. в разделе [Использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Дополнительные сведения о приложениях для управления программированием с помощью поставщика WMI см. в документации по инструментарию WMI в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>См. также статью  
 [Работа с поставщиком WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Использование WQL и языков сценариев с поставщиком WMI для управления конфигурациями](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  

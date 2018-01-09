---
title: "Основные сведения о поставщике WMI для управления конфигурацией | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e2e0302b044ee46b7b207eb5d5408c91f940bfd0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Основные сведения о поставщике WMI для управления конфигурацией
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусматривает поставщик WMI для управления конфигурацией. Это позволяет использовать инструментарий управления Windows для управления службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сетевыми параметрами сервера и его псевдонимами. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]службы, сетевые параметры и псевдонимы представлены объектами инструментария WMI в root\Microsoft\SqlServer\ComputerManagement *nn*  имен компьютера. После установления соединения с поставщиком WMI на некотором компьютере службы сетевые параметры и псевдонимы можно запрашивать с помощью WQL или языка сценариев.  
  
 Поставщик WMI является поставщиком экземпляров. Он поставляет экземпляры [классы WMI](../../relational-databases/wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) и поддерживает следующие асинхронные операции.  
  
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
  
 Примеры управляющего приложения, использующего поставщик WMI для управления конфигурацией см. в разделе [использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Дополнительные сведения о программировании управляющих приложений с помощью поставщика WMI, см. в документации WMI в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>См. также:  
 [Работа с поставщиком WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/working-with-the-wmi-provider-for-configuration-management.md)   
 [Использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией](../../relational-databases/wmi-provider-configuration/using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  

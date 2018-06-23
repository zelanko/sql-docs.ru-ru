---
title: Основные сведения о поставщике WMI для управления конфигурацией | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 459bb3bb7843a0f962d9747ac702da23909ca9fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193076"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Основные сведения о поставщике WMI для управления конфигурацией
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет поставщик WMI для управления конфигурацией. Это позволяет использовать инструментарий управления Windows для управления службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сетевыми параметрами сервера и его псевдонимами. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы, сетевые параметры и псевдонимы представлены объектами инструментария WMI в root\Microsoft\SqlServer\ComputerManagement*nn* имен компьютера. После установления соединения с поставщиком WMI на некотором компьютере службы сетевые параметры и псевдонимы можно запрашивать с помощью WQL или языка сценариев.  
  
 Поставщик WMI является поставщиком экземпляров. Он поставляет экземпляры [классы WMI](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) и поддерживает следующие асинхронные операции.  
  
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
  
 Примеры управляющего приложения, использующего поставщик WMI для управления конфигурацией см. в разделе [использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Дополнительные сведения о программировании управляющих приложений с помощью поставщика WMI, см. в документации WMI в [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.  
  
## <a name="see-also"></a>См. также  
 [Работа с поставщиком WMI для управления конфигурацией](working-with-the-wmi-provider-for-configuration-management.md)   
 [Использование WQL и языков сценариев с поставщиком WMI для управления конфигурациями](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
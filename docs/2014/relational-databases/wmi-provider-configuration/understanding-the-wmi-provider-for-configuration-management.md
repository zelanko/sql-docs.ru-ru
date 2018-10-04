---
title: Основные сведения о поставщике WMI для управления конфигурацией | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 238e8e52ec238e8387fd49d82f15368ef9be3d0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222337"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a>Основные сведения о поставщике WMI для управления конфигурацией
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусматривает поставщик WMI для управления конфигурацией. Это позволяет использовать инструментарий управления Windows для управления службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сетевыми параметрами сервера и его псевдонимами. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы, сетевые параметры и псевдонимы представлены объектами Инструментария в root\Microsoft\SqlServer\ComputerManagement*nn* имен компьютера. После установления соединения с поставщиком WMI на некотором компьютере службы сетевые параметры и псевдонимы можно запрашивать с помощью WQL или языка сценариев.  
  
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
  
 Примеры управляющего приложения, использующего поставщик WMI для управления конфигурацией, см. в разделе [использование WQL и языков сценариев с поставщиком WMI для управления конфигурацией](using-wql-and-scripting-languages-with-the-wmi-provider.md).  
  
 Дополнительные сведения о программировании управляющих приложений с помощью поставщика WMI, см. в разделе документации по инструментарию WMI в [!INCLUDE[msCoName](../../includes/msconame-md.md)] пакета SDK для .NET Framework.  
  
## <a name="see-also"></a>См. также  
 [Работа с поставщиком WMI для управления конфигурацией](working-with-the-wmi-provider-for-configuration-management.md)   
 [Использование WQL и языков сценариев с поставщиком WMI для управления конфигурациями](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  

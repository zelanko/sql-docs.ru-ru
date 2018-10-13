---
title: Диспетчер WMI-соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 406faef2e7d2392776370f3fb5da49daf3dc175a
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119122"
---
# <a name="wmi-connection-manager"></a>Диспетчер WMI-соединений
  Диспетчер WMI-соединений позволяет использовать в пакетах службу инструментария управления Windows (WMI) для управления данными в корпоративной среде. Задача «Веб-служба», которую включают в себя службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует диспетчер WMI-соединений.  
  
 При добавлении к пакету диспетчер WMI-соединений [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер, который будет разрешен в соединение WMI во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений для соединений `Connections` пакета . Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `WMI`.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Настройка диспетчера WMI-соединений  
 Чтобы настроить диспетчер WMI-соединений, выполните следующее:  
  
-   Задайте имя учетной записи.  
  
-   Задайте пространство имен на сервере.  
  
-   Выберите режим проверки подлинности для соединения с сервером.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера WMI-сеансов](../wmi-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Задача «Веб-служба»](../control-flow/web-service-task.md)   
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  

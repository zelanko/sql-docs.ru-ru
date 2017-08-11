---
title: "Диспетчер WMI-соединений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.wmiconnection.f1
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: 6e314655d6a230bde897ffceb54fadb8d180d1db
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="wmi-connection-manager"></a>Диспетчер WMI-соединений
  Диспетчер WMI-соединений позволяет использовать в пакетах службу инструментария управления Windows (WMI) для управления данными в корпоративной среде. Задача «Веб-служба», которую включают в себя службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует диспетчер WMI-соединений.  
  
 При добавлении к пакету диспетчера подключений WMI [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который будет разрешен в соединение WMI во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **WMI**.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Настройка диспетчера WMI-соединений  
 Чтобы настроить диспетчер WMI-соединений, выполните следующее:  
  
-   Задайте имя учетной записи.  
  
-   Задайте пространство имен на сервере.  
  
-   Выберите режим проверки подлинности для соединения с сервером.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера WMI-сеансов](../../integration-services/connection-manager/wmi-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="wmi-connection-manager-editor"></a>редактор диспетчера WMI-сеансов
  Диалоговое окно **Диспетчер WMI-соединений** позволяет выбрать соединение инструментария управления Windows (Microsoft WMI) к серверу.  
  
 Дополнительные сведения о диспетчере WMI-сеансов см. в разделе [WMI Connection Manager](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Название**  
 Задает уникальное имя диспетчера соединений.  
  
 **Description**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Имя сервера**  
 Введите имя сервера, с которым требуется установить WMI-сеанс.  
  
 **Пространство имен**  
 Укажите пространство имен инструментария WMI.  
  
 **Использовать проверку подлинности Windows**  
 Выберите этот режим для проверки подлинности Windows. При использовании проверки подлинности Windows не будет необходимости ввода имени пользователя и пароля для установки соединения.  
  
 **Имя пользователя**  
 Если проверка подлинности Windows не используется, необходимо ввести имя пользователя для данного соединения.  
  
 **Пароль**  
 Если проверка подлинности Windows не используется, необходимо ввести пароль для данного соединения.  
  
 **Тест**  
 Проверка настроек диспетчера соединений.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Веб-служба»](../../integration-services/control-flow/web-service-task.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../integration-services/connection-manager/integration-services-ssis-connections.md)  


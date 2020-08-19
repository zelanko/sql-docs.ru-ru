---
description: Диспетчер WMI-соединений
title: Диспетчер WMI-соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.wmiconnection.f1
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0bb36af50d48fb0155c85a1662b4dd4780f3f03d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425956"
---
# <a name="wmi-connection-manager"></a>Диспетчер WMI-соединений

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Диспетчер WMI-соединений позволяет использовать в пакетах службу инструментария управления Windows (WMI) для управления данными в корпоративной среде. Задача "Веб-служба", которую включают в себя службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], использует диспетчер WMI-соединений.  
  
 Когда вы добавляете диспетчер подключений WMI в пакет, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который будет разрешен в соединение WMI во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **WMI**.  
  
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
 **имя**;  
 Задает уникальное имя диспетчера соединений.  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Имя сервера**  
 Введите имя сервера, с которым требуется установить WMI-сеанс.  
  
 **Пространство имен**  
 Укажите пространство имен инструментария WMI.  
  
 **Использовать проверку подлинности Windows**  
 Выберите этот режим для проверки подлинности Windows. При использовании проверки подлинности Windows не будет необходимости ввода имени пользователя и пароля для установки соединения.  
  
 **User name**  
 Если проверка подлинности Windows не используется, необходимо ввести имя пользователя для данного соединения.  
  
 **Пароль**  
 Если проверка подлинности Windows не используется, необходимо ввести пароль для данного соединения.  
  
 **Тест**  
 Проверка настроек диспетчера соединений.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Веб-служба»](../../integration-services/control-flow/web-service-task.md)   
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  

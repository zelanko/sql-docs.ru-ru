---
title: "Разрешения, необходимые службе CDC для соединения с SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1556a9f29ba5746fdd4a5a721602b01c1cc54c58
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Разрешения, необходимые службе CDC для соединения с SQL Server
  Для консоли настройки службы CDC требуются сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения соответствующих задач. В этом разделе описываются сведения, которые можно указать в диалоговом окне «Подключение к SQL Server» для настройки подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Диалоговое окно «Подключение к SQL Server» открывается при необходимости, например когда сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отсутствуют или когда они имеются, но для подключения нет требуемых разрешений.  
  
 В следующей таблице приведено описание различных задач, в рамках которых требуется подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также необходимых разрешений для имени пользователя/пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Задача|Минимальные разрешения|  
|----------|-------------------------|  
|Подготовка экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`dbcreator` предопределенная роль сервера|  
|Создание имени входа службы Oracle CDC и SQL Server для использования службой Oracle CDC.|`public` предопределенная роль сервера|  
|Создание имени входа службы Oracle CDC, которое будет использоваться для регистрации службы в MSXDBCDC.|`db_datareader` и `db_datawriter` в MSXDBCDC|  
|Изменение имени входа службы Oracle CDC так, чтобы оно могло использоваться для обновления регистрации службы в MSXDBCDC.|`db_datareader` и `db_datawriter` в MSXDBCDC|  
|Удаление имени входа службы Oracle CDC, предназначенного для обновления регистрации службы в MSXDBCDC.|`db_datareader` и `db_datawriter` в MSXDBCDC|  
  
## <a name="see-also"></a>См. также:  
 [Соединение с SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md)   
 [Соединение с SQL Server для удаления](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  

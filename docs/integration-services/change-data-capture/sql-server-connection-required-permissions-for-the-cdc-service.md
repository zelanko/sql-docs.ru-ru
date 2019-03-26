---
title: Разрешения, необходимые службе CDC для соединения с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 84037e98c5ff29465e46c247421bee65c4990174
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58276993"
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
  
  

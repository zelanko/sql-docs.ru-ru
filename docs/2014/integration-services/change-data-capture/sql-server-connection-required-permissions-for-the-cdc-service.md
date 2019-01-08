---
title: Разрешения, необходимые службе CDC для соединения с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 83b87ac1bbe7997843eed4fc5b9b0948ef614fd1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769126"
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
  
## <a name="see-also"></a>См. также  
 [Соединение с SQL Server](connection-to-sql-server.md)   
 [Соединение с SQL Server для удаления](connection-to-sql-server-for-delete.md)  
  
  

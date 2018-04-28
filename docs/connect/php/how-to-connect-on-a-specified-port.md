---
title: 'Как: подключение к заданному порту | Документы Microsoft'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b17dd2bb8df3f7274cb8eea36faf3ee5f320f983
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-connect-on-a-specified-port"></a>Практическое руководство. Подключение к заданному порту
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Этот раздел описывает подключение к SQL Server по указанном порту с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Порядок подключения к заданному порту  
  
1.  Проверьте порт, через который сервер настроен принимать подключения. Сведения о настройке сервера на прием подключений через указанный порт см. в разделе [как: Настройка сервера для прослушивания определенного TCP-порта (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Добавьте нужный порт в *$serverName* параметр [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) функции. Разделите имя сервера и порт запятой. Например, в следующих строках кода драйвер SQLSRV используется для демонстрации подключения к серверу с именем *myServer* через порт 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    В следующих строках кода используется драйвер PDO_SQLSRV для демонстрации подключения к серверу с именем *myServer* через порт 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>См. также  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  

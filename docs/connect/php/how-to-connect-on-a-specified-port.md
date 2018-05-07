---
title: 'Как: подключение к заданному порту | Документы Microsoft'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c744ded8b11ea659d632e996a611edb5e2ec70c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  

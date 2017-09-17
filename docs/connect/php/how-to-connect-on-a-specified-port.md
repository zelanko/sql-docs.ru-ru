---
title: "Как: подключение к заданному порту | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 88115d77c56cafed731aa2a9cf6c39afcd191618
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-connect-on-a-specified-port"></a>Практическое руководство. Подключение к заданному порту
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Этот раздел описывает подключение к SQL Server по указанном порту с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Порядок подключения к заданному порту  
  
1.  Проверьте порт, через который сервер настроен принимать подключения. Сведения о настройке сервера на прием подключений через указанный порт см. в разделе [как: Настройка сервера для прослушивания определенного TCP-порта (диспетчер конфигурации SQL Server)](http://go.microsoft.com/fwlink/?LinkId=121865).  
  
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
  
## <a name="see-also"></a>См. также:  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Приступая к работе с драйвером SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md) 
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  


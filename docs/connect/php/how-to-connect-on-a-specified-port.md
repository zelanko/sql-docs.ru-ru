---
title: 'Практическое: подключение к заданному порту | Документация Майкрософт'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4d19077a4a0b676875a9b82acf529cc8720f31f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680026"
---
# <a name="how-to-connect-on-a-specified-port"></a>Практическое руководство. Подключение к заданному порту
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Этот раздел описывает подключение к SQL Server по указанном порту с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Порядок подключения к заданному порту  
  
1.  Проверьте порт, через который сервер настроен принимать подключения. Дополнительные сведения о настройке сервера для приема подключений через указанный порт см. в статье [Практическое руководство. Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Добавьте нужный порт в параметр *$serverName* функции [sqlsrv_connect](../../connect/php/sqlsrv-connect.md). Разделите имя сервера и порт запятой. Например, в следующих строках кода драйвер SQLSRV используется для демонстрации подключения к серверу с именем *myServer* через порт 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    В следующих строках кода драйвер PDO_SQLSRV используется для демонстрации подключения к серверу с именем *myServer* через порт 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>См. также:  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Приступая к работе с драйверами Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  

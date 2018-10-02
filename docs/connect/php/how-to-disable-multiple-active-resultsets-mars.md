---
title: Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0095953a9fc6b70f0776b438af567260a9f749c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686104"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Если необходимо подключиться к источнику данных SQL Server, который не включает множественные активные результирующие наборы (MARS), можно использовать параметр подключения MultipleActiveResultSets для отключения или включения функции MARS.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-disable-mars-support"></a>Отключение поддержки функции MARS  
  
-   Используйте следующий параметр подключения:  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    Если приложение пытается выполнить запрос для подключения с открытым активным результирующим набором, при второй попытке выполнения запроса возвращаются следующие сведения об ошибке:  
  
    Подключение не может обработать эту операцию, поскольку отсутствует инструкция с ожидающими результатами.  Чтобы сделать подключение доступным для других запросов, извлеките все результаты, отмените инструкцию или освободите ее. Дополнительные сведения о параметре подключения MultipleActiveResultSets см. в статье [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="example"></a>Пример  
Следующий пример показывает, как отключить поддержку функции MARS с помощью драйвера SQLSRV из [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'MultipleActiveResultSets'=> false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Пример  
В приведенном ниже примере показано, как отключить поддержку функции MARS с помощью драйвера PDO_SQLSRV из [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
// Connect to the local server using Windows Authentication and AdventureWorks database  
$serverName = "(local)";   
$database = "AdventureWorks";  
  
try {  
   $conn = new PDO(" sqlsrv:server=$serverName ; Database=$database ; MultipleActiveResultSets=false ", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
$conn = null;   
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)  
  

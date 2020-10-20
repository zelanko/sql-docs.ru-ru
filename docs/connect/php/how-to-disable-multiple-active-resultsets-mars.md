---
title: Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS)
description: Узнайте, как отключить поддержку множественных активных результирующих наборов при использовании драйверов Майкрософт для PHP для SQL Server
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11ca08618f0b8d7675e8ec74ec259d4225d44aba
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2020
ms.locfileid: "92080623"
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
  
## <a name="sqlsrv-example"></a>Пример SQLSRV  
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
  
## <a name="pdo_sqlsrv-example"></a>Пример PDO_SQLSRV  
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
  

---
title: "sqlsrv_connect | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
caps.latest.revision: 67
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e9491e2b0721f7c7a2ca6b5ed37c52135a4c760
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Создает ресурс подключения и открывает соединение. По умолчанию выполняется попытка установки соединения с использованием проверки подлинности Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>Параметры  
*$serverName*: строка, указывающая имя сервера, с которым устанавливается соединение. В состав этой строки можно включить имя экземпляра (например, "мой_сервер\имя_экземпляра") или номер порта (например, "мой_сервер, 1521"). Полное описание значений, доступных для этого параметра, см. в разделе "Ключевые слова в строке подключения драйвера ODBC" статьи [Использование ключевых слов строки подключения с SQL Native Client](http://go.microsoft.com/fwlink/?LinkId=105504).  
  
Начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], можно также указать экземпляр LocalDB с `"(localdb)\instancename"`. Дополнительные сведения см. в статье [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).  
  
Кроме того, начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], можно указать имя виртуальной сети для подключения к группе доступности AlwaysOn. Дополнительные сведения о поддержке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] для [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]см. в статье [Поддержка высокой доступности и аварийного восстановления в драйвере PHP для SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).  
  
*$connectionInfo* [необязательно]: ассоциативный **массива** , содержащий атрибуты соединения (например, **массива**(«Database» = > «AdventureWorks»)). Список поддерживаемых ключей для массива см. в статье [Connection Options](../../connect/php/connection-options.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс подключения PHP. Если не удается успешно создать и открыть соединение, возвращается значение **false** .  
  
## <a name="remarks"></a>Замечания  
Если значения для ключей *UID* и *PWD* не указаны в необязательном параметре *$connectionInfo* , предпринимается попытка установки соединения с использованием проверки подлинности Windows. Дополнительные сведения о подключении к серверу см. в статьях [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) и [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Пример  
Следующий пример создает и открывает соединение с использованием проверки подлинности Windows. В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://www.codeplex.com/SqlServerSamples) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Connecting to the Server](../../connect/php/connecting-to-the-server.md)  
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  


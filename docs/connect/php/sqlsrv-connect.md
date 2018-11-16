---
title: sqlsrv_connect | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8df39220a9d3ee2286e4ed86610790e20a3b78c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601194"
---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Создает ресурс подключения и открывает соединение. По умолчанию выполняется попытка установки соединения с использованием проверки подлинности Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>Параметры  
*$serverName*: строка, указывающая имя сервера, с которым устанавливается соединение. В состав этой строки можно включить имя экземпляра (например, "мой_сервер\имя_экземпляра") или номер порта (например, "мой_сервер, 1521"). Полное описание значений, доступных для этого параметра, см. в разделе "Ключевые слова в строке подключения драйвера ODBC" статьи [Использование ключевых слов строки подключения с SQL Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
Начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], можно также указать экземпляр LocalDB с `"(localdb)\instancename"`. Дополнительные сведения см. в разделе [поддержка LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).  
  
Кроме того, начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], можно указать имя виртуальной сети для подключения к группе доступности AlwaysOn. Дополнительные сведения о [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержка [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).  
  
*$connectionInfo* (необязательно): ассоциативный **массив**, содержащий атрибуты соединения (например, **array**("Database" => "AdventureWorks")). Список поддерживаемых ключей для массива см. в статье [Connection Options](../../connect/php/connection-options.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс подключения PHP. Если не удается успешно создать и открыть соединение, возвращается значение **false** .  
  
## <a name="remarks"></a>Remarks  
Если значения для ключей *UID* и *PWD* не указаны в необязательном параметре *$connectionInfo* , предпринимается попытка установки соединения с использованием проверки подлинности Windows. Дополнительные сведения о подключении к серверу см. в статьях [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) и [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Пример  
Следующий пример создает и открывает соединение с использованием проверки подлинности Windows. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://www.codeplex.com/SqlServerSamples) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  

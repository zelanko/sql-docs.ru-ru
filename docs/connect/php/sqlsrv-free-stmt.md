---
title: sqlsrv_free_stmt | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_free_stmt
apitype: NA
helpviewer_keywords:
- sqlsrv_free_stmt
- API Reference, sqlsrv_free_stmt
ms.assetid: 3c71f432-36ad-41e1-8ac7-587c82539448
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7188935f0466a58c444f72e02ce541a646e1b41f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610765"
---
# <a name="sqlsrvfreestmt"></a>sqlsrv_free_stmt
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Освобождает все ресурсы, связанные с указанной инструкцией. Инструкцию нельзя использовать повторно после вызова этой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_free_stmt( resource $stmt)  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: закрываемая инструкция.  
  
## <a name="return-value"></a>Возвращаемое значение  
Логическое значение **true** , если только функция не вызывается с недопустимым параметром. Если функция вызывается с недопустимым параметром, возвращается значение **false** .  
  
> [!NOTE]  
> **Null** является допустимым параметром для этой функции. Это позволяет несколько раз вызывать функцию в скрипте. Например, если освободить инструкцию в условии ошибки, а затем снова освободить ее в конце сценария, второй вызов**sqlsrv_free_stmt** возвратит значение **true** (истина), так как первый вызов **sqlsrv_free_stmt** (в условии ошибки) задал для ресурса инструкции значение **null**.  
  
## <a name="example"></a>Пример  
Следующий пример создает ресурс инструкции, выполняется простой запрос и вызывает **sqlsrv_free_stmt** , чтобы освободить все ресурсы, связанные с инструкцией. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM Person.Contact");  
if( $stmt )  
{  
     echo "Statement executed.\n";  
}  
else  
{  
     echo "Query could not be executed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*-------------------------------  
     Process query results here.  
-------------------------------*/  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)  
  

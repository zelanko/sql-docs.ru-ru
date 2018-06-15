---
title: sqlsrv_errors | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_errors
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_errors
- sqlsrv_errors
- errors and warnings
ms.assetid: d1fcffec-f34f-46de-9a0e-343f3b5dbae2
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e097a5b89d708b3a91296c49c0c615f8955b96cb
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309053"
---
# <a name="sqlsrverrors"></a>sqlsrv_errors
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает расширенные ошибки или ошибки и предупреждения о последней **sqlsrv** выполненной операции.  
  
**Sqlsrv_errors** функция может вернуть ошибки или ошибки и предупреждения путем вызова с одним из значений параметров, указанных в разделе "Параметры" ниже.  
  
По умолчанию предупреждения, созданные при вызове любой функции **sqlsrv** , обрабатываются как ошибки; при возникновении предупреждения во время вызова функции **sqlsrv** она возвращает значение false. Однако предупреждения, которые соответствуют значениям SQLSTATE 01000, 01001, 01003 и 01S02, никогда не обрабатываются как ошибки.  
  
Следующая строка кода отключает описанное выше поведение; предупреждение, созданное вызовом функции **sqlsrv** , не приводит к тому, что функция возвращает значение false:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
```  
  
Следующая строка кода позволяет возобновить использование поведения по умолчанию; предупреждения (с учетом перечисленных выше исключений) обрабатываются как ошибки:  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 1);  
```  
  
Независимо от настройки предупреждения можно извлечь только путем вызова **sqlsrv_errors** либо **SQLSRV_ERR_ALL** или **SQLSRV_ERR_WARNINGS** значение параметра (см. Параметры ниже подробные сведения).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_errors( [int $errorsAndOrWarnings] )  
```  
  
#### <a name="parameters"></a>Параметры  
*$errorsAndOrWarnings*[необязательно]: Предопределенная константа. Этот параметр может принимать одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Возвращаются ошибки и предупреждения, созданные при последнем вызове функции **sqlsrv** .|  
|SQLSRV_ERR_ERRORS|Возвращаются ошибки, созданные при последнем вызове функции **sqlsrv** .|  
|SQLSRV_ERR_WARNINGS|Возвращаются предупреждения, созданные при последнем вызове функции **sqlsrv** .|  
  
Если значение параметра не указано, возвращаются ошибки и предупреждения, созданные при последнем вызове функции **sqlsrv** .  
  
## <a name="return-value"></a>Возвращаемое значение  
**Массив** массивов или значение **null**. Каждый **массива** в возвращаемом **массива** содержит три пары ключ значение. Следующая таблица содержит все ключи и их описания.  
  
|Key|Описание|  
|-------|---------------|  
|SQLSTATE|Для ошибок, возникших в драйвере ODBC, SQLSTATE, возвращенный ODBC. Сведения о значениях SQLSTATE для ODBC см. в разделе [коды ошибок ODBC](../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).<br /><br />Для ошибок, возникших в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], SQLSTATE для IMSSP.<br /><br />Для предупреждений, возникших в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], SQLSTATE для 01SSP.|  
|код|Для ошибок, возникших в SQL Server, собственный код ошибки SQL Server.<br /><br />Для ошибок, возникших в драйвере ODBC, код ошибки, возвращенный ODBC.<br /><br />Для ошибок, возникших в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], код ошибки [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] . Дополнительные сведения см. в статье [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md).|  
|message|Описание ошибки.|  
  
Доступ к значениям массива можно также осуществить с помощью числовых ключей 0, 1 и 2. Если ошибки или предупреждения отсутствуют, возвращается значение **null** .  
  
## <a name="example"></a>Пример  
Следующий пример отображает ошибки, возникающие при сбое выполнения инструкции. (Инструкция завершается ошибкой, поскольку **InvalidColumName** не является допустимым именем столбца в указанной таблице.) Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Set up a query to select an invalid column name. */  
$tsql = "SELECT InvalidColumnName FROM Sales.SalesOrderDetail";  
  
/* Attempt execution. */  
/* Execution will fail because of the invalid column name. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
      if( ($errors = sqlsrv_errors() ) != null)  
      {  
         foreach( $errors as $error)  
         {  
            echo "SQLSTATE: ".$error[ 'SQLSTATE']."\n";  
            echo "code: ".$error[ 'code']."\n";  
            echo "message: ".$error[ 'message']."\n";  
         }  
      }  
}  
  
/* Free connection resources */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  

---
title: "PDOStatement::bindParam | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 02d31959423de5c0df4dc06e9caa16ea983ef000
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Привязывает параметр к именованному заполнителю или заполнителю с вопросительным знаком в инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::bindParam( $parameter, &$variable [,$data_type[, $length[, $driver_options]]] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*параметр*: идентификатор параметра (смешанное). Для инструкции, использующей именованные заполнители, это имя параметра (:name). Для подготовленной инструкции, использующей синтаксис с вопросительным знаком, это начинающийся с 1 индекс параметра.  
  
&$*переменная*: имя (смешанное) переменной PHP, привязываемой к параметру инструкции SQL.  
  
$*data_type*: константа PDO::PARAM_ * необязательно (целое число). Значение по умолчанию — PDO::PARAM_STR.  
  
$*Длина*: длина типа данных необязательно (целое число). Можно задать PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE, чтобы указать размер по умолчанию при использовании PDO::PARAM_INT или PDO::PARAM_BOOL в $*data_type*.  
  
$*driver_options*: необязательные параметры драйвера (смешанное). Например, можно указать PDO::SQLSRV_ENCODING_UTF8 для привязки столбца к переменной в виде строки с кодировкой UTF-8.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Замечания  
При привязке к столбцам сервера, имеющим тип varbinary, binary или varbinary(max) пустых данных следует указать двоичную кодировку (PDO::SQLSRV_ENCODING_BINARY) с помощью $*driver_options*. Дополнительные сведения о кодировании констант см. в статье [Константы](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md) .  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример кода показывает, что после привязки значения $contact к параметру изменение этого значения приводит к изменению значения, передаваемого в запрос.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Пример  
Этот пример кода показывает, как получить доступ к параметру вывода.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(* ) from Sys.tables");  
$stmt->bindParam( 1, $input1, PDO::PARAM_STR, 10 );  
$stmt->execute();  
echo $input1;  
?>  
```  
  
## <a name="example"></a>Пример  
Этот пример кода показывает, как получить доступ к параметру ввода/вывода.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  


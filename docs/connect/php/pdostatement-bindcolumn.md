---
title: PDOStatement::bindColumn | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4b159e57f6f2335e894490f7e34d159bd95b2b6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993131"
---
# <a name="pdostatementbindcolumn"></a>PDOStatement::bindColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Привязывает переменную к столбцу в результирующем наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*column*: номер (смешанные значения) столбца (с индексами от 1) или его имя в результирующем наборе.  
  
&$*param*: имя (смешанные значения) переменной PHP, к которой будет привязан столбец.  
  
$*type*: необязательный тип данных параметра, представленный константой PDO::PARAM_*.  
  
$*maxLen*: необязательное целое число, не используемое драйверами Майкрософт для PHP для SQL Server.  
  
$*driverdata*: необязательные смешанные параметры для драйвера. Например, можно указать PDO::SQLSRV_ENCODING_UTF8 для привязки столбца к переменной в виде строки с кодировкой UTF-8.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример показывает, как можно привязать переменную к столбцу в результирующем наборе.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

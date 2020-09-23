---
title: PDOStatement::rowCount
description: Справочник по API для функции PDOStatement::rowCount в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0569f26a-2376-4c20-8813-bd3c87d0ae9f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31671bc3db85a31cde4109cedb11f3ab44f07ea1
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646584"
---
# <a name="pdostatementrowcount"></a>PDOStatement::rowCount
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает число строк, добавленных, удаленных или измененных при выполнении последней инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int PDOStatement::rowCount ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Число добавленных, удаленных или измененных строк.  
  
## <a name="remarks"></a>Remarks  
Если последней инструкцией SQL, выполненной связанным PDOStatement, была инструкция SELECT, курсор PDO::CURSOR_FWDONLY возвращает значение -1. Курсор PDO::CURSOR_SCROLLABLE возвращает количество строк в результирующем наборе.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере показано два варианта использования rowCount. В первом варианте возвращается число строк, которые были добавлены в таблицу. Во втором варианте показано, что rowCount может возвращать количество строк в результирующем наборе при указании прокручиваемого курсора.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table2(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
  
echo "\n\n";  
  
$con = null;  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
print $stmt->rowCount();  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

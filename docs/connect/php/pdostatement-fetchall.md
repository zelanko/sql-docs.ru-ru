---
title: PDOStatement::fetchAll
description: Справочник по API для функции PDOStatement::fetchAll в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: be74188a-77cd-4d19-b16e-77278373c979
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c3ab50febea25e68b634d2f2afeb6a20b71bf82
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645101"
---
# <a name="pdostatementfetchall"></a>PDOStatement::fetchAll
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает строки в результирующем наборе в виде массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDOStatement::fetchAll([ $fetch_style[, $column_index ][, ctor_args]] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*fetch_style*: символ (целое число), указывающий формат строки данных. Список значений см. в статье [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) . Также разрешено использовать PDO::FETCH_COLUMN. Значение по умолчанию — PDO::FETCH_BOTH.  
  
$*column_index*: целое число, представляющее возвращаемый столбец, если $*fetch_style* имеет значение PDO::FETCH_COLUMN. Значение по умолчанию равно 0.  
  
$*ctor_args*: массив параметров для конструктора классов, если $*fetch_style* имеет значение PDO::FETCH_CLASS или PDO::FETCH_OBJ.  
  
## <a name="return-value"></a>Возвращаемое значение  
Массив оставшихся строк в результирующем наборе или значение false, если вызов метода завершается ошибкой.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_BOTH);  
   print_r( $result );  
   print "\n-----------\n";  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_NUM);  
   print_r( $result );  
   print "\n-----------\n";  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_COLUMN, 1);  
   print_r( $result );  
   print "\n-----------\n";  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg\n";  
      }  
  
      function __toString() {  
         echo "To string\n";  
      }  
   };  
  
   $stmt = $conn->query( 'SELECT TOP(2) * FROM Person.ContactType' );  
   $all = $stmt->fetchAll( PDO::FETCH_CLASS, 'cc', array( 'Hi!' ));  
   var_dump( $all );  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

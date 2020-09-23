---
title: PDOStatement::execute
description: Справочник по API для функции PDOStatement::execute в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c2e80566-fa41-4918-8521-cf2e05374cbd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 71b9592a35fcc28b302c7aadb1ca5de0c75c3d6c
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645125"
---
# <a name="pdostatementexecute"></a>PDOStatement::execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Выполняет инструкцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::execute ([ $input ] );  
```  
  
#### <a name="parameters"></a>Параметры  
*$input*: ассоциативный массив, содержащий значения для маркеров параметров (необязательно).  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true в случае успеха, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
Инструкции, выполняемые с помощью PDOStatement::execute, необходимо сначала подготовить с помощью [PDO::prepare](../../connect/php/pdo-prepare.md). Статья [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md) содержит сведения о том, как указать выполнение прямой или подготовленной инструкции.  
  
Все значения массива входных параметров обрабатываются как значения PDO::PARAM_STR.  
  
Если подготовленная инструкция содержит маркеры параметров, необходимо вызвать PDOStatement::bindParam, чтобы осуществить привязку переменных PHP к маркерам параметров или передать массив значений параметров, используемых только в качестве входных.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query );  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
  
echo "\n";  
$param = "Owner";  
$query = "select * from Person.ContactType where name = ?";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
?>  
```  
  
> [!NOTE]
> Рекомендуется использовать строки в качестве входных данных при привязке значений к [десятичным или числовым столбцам](../../t-sql/data-types/decimal-and-numeric-transact-sql.md), чтобы обеспечить точность и правильность, поскольку PHP имеет ограниченную точность для [чисел с плавающей запятой](https://php.net/manual/en/language.types.float.php). То же касается и столбцов bigint, особенно в том случае, если значения выходят за пределы диапазона [целых чисел](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

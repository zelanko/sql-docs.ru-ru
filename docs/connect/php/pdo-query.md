---
title: PDO::Query | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6f5e6d4-8ca9-4f06-89ed-de65ad3952a2
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71c5125b2948918a1a0fdefb4884529e8c1703c6
ms.sourcegitcommit: ef7f2540ba731cc6a648005f2773d759df5c6405
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39415533"
---
# <a name="pdoquery"></a>PDO::query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Выполняет SQL-запрос и возвращает результирующий набор в виде объекта PDOStatement.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PDOStatement PDO::query ($statement[, $fetch_style);  
```  
  
#### <a name="parameters"></a>Параметры  
*$statement*: инструкция SQL, которую требуется выполнить.  
  
*$fetch_style*: необязательные дополнительные инструкции по выполнению запроса. Дополнительные сведения см. в разделе "Примечания". $*fetch_style* в PDO::query можно переопределить с помощью $*fetch_style* в PDO::fetch.  
  
## <a name="return-value"></a>Возвращаемое значение  
Если вызов завершается успешно, PDO::query возвращает объект PDOStatement. Если вызов завершается со сбоем, PDO::query создает объект PDOException или возвращает значение false, в зависимости от настройки PDO::ATTR_ERRMODE.  
  
## <a name="exceptions"></a>Исключения  
PDOException.  
  
## <a name="remarks"></a>Remarks  
Запрос с применением PDO::query может выполнять подготовленную инструкцию или выполняться напрямую в зависимости от параметров PDO::SQLSRV_ATTR_DIRECT_QUERY;. Дополнительные сведения см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).  
  
PDO::SQLSRV_ATTR_QUERY_TIMEOUT также влияет на поведение PDO::exec;. Дополнительные сведения: [PDO::setAttribute](../../connect/php/pdo-setattribute.md).  
  
Вы можете указать для $*fetch_style* следующие параметры.  
  
|style|Описание|  
|---------|---------------|  
|PDO::FETCH_COLUMN, *номер*|Запросы данных в указанном столбце. Первый столбец в таблице имеет номер 0.|  
|PDO::FETCH_CLASS, '*имя_класса*', array( *список_аргументов* )|Создает экземпляр класса и назначает имена столбцов свойствам в классе. Если конструктор классов принимает один или несколько параметров, также можно передать *arglist*.|  
|Значение PDO::FETCH_CLASS, "*classname*"|Назначает имена столбцов свойствам в существующем классе.|  
  
Вызовите PDOStatement::closeCursor, чтобы освободить ресурсы базы данных, связанные с объектом PDOStatement, перед повторным вызовом PDO::query.  
  
Объект PDOStatement можно закрыть, присвоив ему значение NULL.  
  
Если все данные в результирующий набор не извлекается, следующий вызов PDO::query не завершается со сбоем.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример показывает несколько запросов.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
$conn->setAttribute( PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 1 );  
  
$query = 'select * from Person.ContactType';  
  
// simple query  
$stmt = $conn->query( $query );  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print_r( $row['Name'] ."\n" );  
}  
  
echo "\n........ query for a column ............\n";  
  
// query for one column  
$stmt = $conn->query( $query, PDO::FETCH_COLUMN, 1 );  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query with a new class ............\n";  
$query = 'select * from HumanResources.Department order by GroupName';  
// query with a class  
class cc {  
   function __construct( $arg ) {  
      echo "$arg";  
   }  
  
   function __toString() {  
      return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
   }  
}  
  
$stmt = $conn->query( $query, PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query into an existing class ............\n";  
$c_obj = new cc( '' );  
$stmt = $conn->query( $query, PDO::FETCH_INTO, $c_obj );  
while ( $stmt->fetch() ){  
   echo "$c_obj\n";  
}  
  
$stmt = null;  
?>  
```

## <a name="example"></a>Пример
В этом примере кода показано, как создать таблицу [sql_variant](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) типов и получения вставляемых данных.

```
<?php
$server = 'serverName';
$dbName = 'databaseName';
$uid = 'yourUserName';
$pwd = 'yourPassword';

$conn = new PDO("sqlsrv:server=$server; database = $dbName", $uid, $pwd);
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  

try {
    $tableName = 'testTable';
    $query = "CREATE TABLE $tableName ([c1_int] sql_variant, [c2_varchar] sql_variant)";

    $stmt = $conn->query($query);
    unset($stmt);

    $query = "INSERT INTO [$tableName] (c1_int, c2_varchar) VALUES (1, 'test_data')";
    $stmt = $conn->query($query);
    unset($stmt);

    $query = "SELECT * FROM $tableName";
    $stmt = $conn->query($query);

    $result = $stmt->fetch(PDO::FETCH_ASSOC);
    print_r($result);
    
    unset($stmt);
    unset($conn);
} catch (Exception $e) {
    echo $e->getMessage();
}
?>
```

Ожидаемый результат будет следующим:

```
Array
(
    [c1_int] => 1
    [c2_varchar] => test_data
)
```

## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

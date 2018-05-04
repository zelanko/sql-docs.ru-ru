---
title: PDO::Prepare | Документы Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4bb96c535fb3962e5c92723bb67d6cd0827de03
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает инструкцию для выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>Параметры  
$*statement*: строка, содержащая инструкцию SQL.  
  
*key_pair*: массив, содержащий имя и значение атрибута. Дополнительные сведения см. в разделе «Примечания».  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успеха возвращает объект PDOStatement. В случае сбоя возвращает объект PDOException или значение false в зависимости от значения PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Замечания  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Не оценивает подготовленную инструкцию до самого выполнения.  
  
В следующей таблице перечислены возможные *key_pair* значения.  
  
|Key|Описание|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Определяет поведение курсора. Значение по умолчанию — PDO::CURSOR_FWDONLY. PDO::CURSOR_SCROLL является статическим курсором.<br /><br />Например, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />При использовании PDO::CURSOR_SCROLL можно использовать описанный ниже PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.<br /><br />В разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41; ](../../connect/php/cursor-types-pdo-sqlsrv-driver.md) Дополнительные сведения о результирующих наборах и курсорах в драйвере PDO_SQLSRV.|  
|PDO::ATTR_EMULATE_PREPARES|При PDO::ATTR_EMULATE_PREPARES заполнителей в подготовленной инструкции заменяется привязанных параметров. Полную инструкцию SQL с заполнителями не передаются в базу данных в инструкции Execute. <br /><br />PDO::ATTR_EMULATE_PREPARES позволяет обойти некоторые ограничения в SQL Server. Например SQL Server не поддерживает именованные или позиционные параметры в некоторые предложения языка Transact-SQL. Кроме того SQL Server существует ограничение в 2100 параметров привязки.<br /><br />Можно задать для атрибута PDO::ATTR_EMULATE_PREPARES значение true. Например:<br /><br />`PDO::ATTR_EMULATE_PREPARES => true`<br /><br />По умолчанию этот атрибут принимает значение false.<br /><br />**Примечание.** При использовании `PDO::ATTR_EMULATE_PREPARES => true`функции обеспечения безопасности параметризованных запросов не работают. Приложение должно убедиться, что данные, привязанные к параметрам не содержит вредоносный код Transact-SQL.<br /><br />**Ограничения:**: поскольку параметры не связаны с помощью функции параметризованного запроса базы данных, input_output и выходные параметры не поддерживаются.|  
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|При значении true задает выполнение прямого запроса. Значение false указывает на выполнение подготовленной инструкции. Дополнительные сведения о PDO::SQLSRV_ATTR_DIRECT_QUERY см. в разделе [выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
При использовании PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL можно использовать PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Например:  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
Следующая таблица содержит возможные значения для PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
|Значение|Описание|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Создает статический клиентский курсор (буферизованный). Дополнительные сведения о клиентских курсорах см. в разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_CURSOR_DYNAMIC|Создает серверный (без буферизации) динамический курсор, который позволяет осуществлять доступ к строкам в любом порядке и будет отражать изменения в базе данных.|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|Создает серверный курсор набора ключей. Курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (удаленная строка возвращается без значений).|  
|PDO::SQLSRV_CURSOR_STATIC|Создает серверный статический курсор, который позволяет осуществлять доступ к строкам в любом порядке, но не будет отражать изменения в базе данных.<br /><br />PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL подразумевает PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC.|  
  
Объект PDOStatement можно закрыть, присвоив ему значение NULL.  
  
## <a name="example"></a>Пример  
Этот пример показывает, как использовать метод PDO::prepare с маркерами параметров и курсором последовательного доступа.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  
  
## <a name="example"></a>Пример  
Этот пример показывает, как использовать метод PDO::prepare с клиентским курсором. Пример, показывающий серверный курсор, в разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

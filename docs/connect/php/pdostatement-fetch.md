---
title: PDOStatement::fetch | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 499175b3e75c27b82df93ef84f8b17a049265356
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308423"
---
# <a name="pdostatementfetch"></a>PDOStatement::fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает строку из результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*fetch_style*: символ необязательно (целое число), указывающий формат строки данных. В разделе «Примечания» в список возможных значений для $*fetch_style*. Значение по умолчанию — PDO::FETCH_BOTH. $*fetch_style* в fetch переопределяет $ метод*fetch_style* указанные в методе PDO::query.  
  
$*cursor_orientation*: символ необязательно (целое число), указывающий строку для получения, когда Подготовленная инструкция указывает `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`. В разделе «Примечания» в список возможных значений для $*cursor_orientation*. Пример использования прокручиваемого курсора см. в статье [PDO::prepare](../../connect/php/pdo-prepare.md) .  
  
$*cursor_offset*: символ необязательно (целое число), определяющее строку, когда $*cursor_orientation* имеет значение PDO::FETCH_ORI_ABS или PDO::FETCH_ORI_REL и PDO::ATTR_CURSOR имеет значение PDO::CURSOR_SCROLL.  
  
## <a name="return-value"></a>Возвращаемое значение  
Смешанное значение, которое возвращает строку или значение false.  
  
## <a name="remarks"></a>Примечания  
Курсор автоматически перемещается вперед при вызове fetch. Следующая таблица содержит список возможных $*fetch_style* значения.  
  
|$*fetch_style*|Описание|  
|-------------------|---------------|  
|PDO::FETCH_ASSOC|Указывает массив, индексированный по имени столбца.|  
|PDO::FETCH_BOTH|Указывает массив, индексированный по имени столбца и с отчетом от нуля. Это значение по умолчанию.|  
|PDO::FETCH_BOUND|Возвращает значение true и присваивает значения, как указывает [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md).|  
|PDO::FETCH_CLASS|Создает экземпляр и сопоставляет столбцы с именованными свойствами.<br /><br />Вызовите [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) перед вызовом fetch.|  
|PDO::FETCH_INTO|Обновляет экземпляр запрошенного класса.<br /><br />Вызовите [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) перед вызовом fetch.|  
|PDO::FETCH_LAZY|Создает имена переменных во время доступа, а также объект без имени.|  
|PDO::FETCH_NUM|Указывает массив, индексируемый по столбцам с отчетом от нуля.|  
|PDO::FETCH_OBJ|Указывает объект без имени с именами свойств, сопоставленными с именами столбцов.|  
  
Если курсор находится в конце результирующего набора (последняя строка была извлечена, и курсор вышел за границу результирующего набора) и является курсором последовательного доступа (PDO::ATTR_CURSOR = PDO::CURSOR_FWDONLY), последующий вызов fetch завершается с ошибкой.  
  
Если курсор является прокручиваемым (PDO::ATTR_CURSOR = PDO::CURSOR_SCROLL), fetch перемещает курсор в пределах границ результирующего набора. Следующая таблица содержит список возможных $*cursor_orientation* значения.  
  
|$*cursor_orientation*|Описание|  
|--------------------------|---------------|  
|PDO::FETCH_ORI_NEXT|Извлекает следующую строку. Это значение по умолчанию.|  
|PDO::FETCH_ORI_PRIOR|Извлекает предыдущую строку.|  
|PDO::FETCH_ORI_FIRST|Извлекает первую строку.|  
|PDO::FETCH_ORI_LAST|Извлекает последнюю строку.|  
|Значение PDO::FETCH_ORI_ABS, *num*|Извлекает строку, запрашиваемую в $*cursor_offset* по номеру строки.|  
|PDO::FETCH_ORI_REL, *num*|Извлекает строку, запрашиваемую в $*cursor_offset* по положению относительно текущей позиции.|  
  
Если значение, указанное для $*cursor_offset* или $*cursor_orientation* приводит к выходу за границу результирующего набора, fetch завершается с ошибкой.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

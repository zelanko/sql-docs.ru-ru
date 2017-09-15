---
title: "PDOStatement::bindValue | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c006ba33bad8d0afb010b0f0bbe316d7a5e3e28f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Привязывает значение к именованному заполнителю или заполнителю с вопросительным знаком в инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::bindValue( $parameter, $value [,$data_type] );  
```  
  
#### <a name="parameters"></a>Параметры  
$*параметр*: идентификатор параметра (смешанное). Для инструкции, использующей именованные заполнители, это имя параметра (:name). Для подготовленной инструкции, использующей синтаксис с вопросительным знаком, это начинающийся с 1 индекс параметра.  
  
$*значение*: значение (смешанное) для привязки к параметру.  
  
$*data_type*: тип данных необязательно (целое число), представленный константой PDO::PARAM_ *. Значение по умолчанию — PDO::PARAM_STR.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Замечания  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере показано, что после привязки значения $contact его изменение не приводит к изменению значения, передаваемого в запрос.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  


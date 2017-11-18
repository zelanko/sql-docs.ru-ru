---
title: "PDOStatement::fetchObject | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ad1932-cab3-4c29-8950-f5e82547d3b5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef6da712209e34e6fcd62ca9436ac16cf3342fea
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementfetchobject"></a>PDOStatement::fetchObject
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает следующую строку в качестве объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDOStatement::fetchObject([ $class_name[,$ctor_args ]] )  
```  
  
#### <a name="parameters"></a>Параметры  
$*class_name*: необязательная строка, задающая имя для создаваемого класса. Значение по умолчанию — stdClass.  
  
$*ctor_args*: необязательный массив с аргументами для конструктора пользовательских классов.  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успешного выполнения возвращает объект с экземпляром данного класса. Свойства сопоставляются со столбцами. Возвращает значение false в случае неудачи.  
  
## <a name="remarks"></a>Замечания  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchObject();  
   print $result->Name;  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  


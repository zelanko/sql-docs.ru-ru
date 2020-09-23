---
title: PDOStatement::fetchObject
description: Справочник по API для функции PDOStatement::fetchObject в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 71ad1932-cab3-4c29-8950-f5e82547d3b5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 459505e3c00a85b6e879e89a3a3b21fb8b3fcf9c
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645874"
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
  
## <a name="remarks"></a>Remarks  
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

[PDO](https://php.net/manual/book.pdo.php)  
  

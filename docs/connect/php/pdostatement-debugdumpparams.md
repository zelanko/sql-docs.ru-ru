---
title: PDOStatement::d Ебугдумппарамс | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf156d65-d933-4235-b89a-18e172d61c15
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c5584d645bc506d1399a47852bed481791988623
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993089"
---
# <a name="pdostatementdebugdumpparams"></a>PDOStatement::debugDumpParams
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Отображает подготовленную инструкцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::debugDumpParams();  
```  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = "Owner";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = :param");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
  
echo "\n\n";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

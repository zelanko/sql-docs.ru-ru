---
title: Метод PDOStatement::errorCode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6a5d32c29368dc141a12ae6eb300137b91935fb3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780470"
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает значение SQLSTATE последней операции в объекте инструкции базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает пятисимвольный SQLSTATE в виде строки или значение NULL в случае отсутствия операции для дескриптора инструкции.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере показан SQL-запрос, который содержит ошибку.  Затем отображается код ошибки.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

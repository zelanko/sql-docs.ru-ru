---
title: PDOStatement::errorCode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1092f1736c4d217a3e875a7df8060b0f722fd080
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907915"
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
  

---
title: PDO::errorCode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9846867cfc6bd50568440c5c66711457754af50c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993281"
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode извлекает значение SQLSTATE последней операции для дескриптора базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
PDO::errorCode возвращает пятисимвольный SQLSTATE в виде строки или значение NULL в случае отсутствия операции для дескриптора базы данных.  
  
## <a name="remarks"></a>Remarks  
Для некоторых успешных операций PDO::errorCode в драйвере PDO_SQLSRV возвращает предупреждения. Например, для успешного подключения PDO::errorCode возвращает значение "01000", указывающее SQL_SUCCESS_WITH_INFO.  
  
PDO::errorCode возвращает только сведения об ошибках для операций, выполненных непосредственно для подключения к базе данных. Если вы создаете экземпляр PDOStatement через PDO::prepare или PDO::query и для объекта инструкции формируется ошибка, PDO::errorCode не получает эту ошибку. Необходимо вызвать метод PDOStatement::errorCode, чтобы возвратить код ошибки для операции, выполненной с определенным объектом инструкции.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере неправильно указано имя столбца (`Cityx` вместо `City`), что вызывает ошибку, о которой затем сообщается.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

---
title: PDO::errorInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab46786bf62f7bd582aa09be562cc3db4183e5c2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919362"
---
# <a name="pdoerrorinfo"></a>PDO::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает расширенные сведения об ошибке для последней операции с дескриптором базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDO::errorInfo();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Массив сведений об ошибке для последней операции с дескриптором базы данных. Этот массив состоит из следующих полей:  
  
-   Код ошибки SQLSTATE.  
  
-   Код ошибки, относящийся к драйверу.  
  
-   Сообщение об ошибке, относящееся к драйверу.  
  
Если ошибка отсутствует или не задано SQLSTATE, то поля, относящиеся к драйверу, будут иметь значение NULL.  
  
## <a name="remarks"></a>Remarks  
PDO::errorInfo возвращает только сведения об ошибках для операций, выполненных непосредственно в базе данных. Используйте PDOStatement::errorInfo при создании экземпляра PDOStatement с помощью PDO::prepare или PDO::query.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере неправильно указано имя столбца (`Cityx` вместо `City`), что вызывает ошибку, о которой затем сообщается.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
echo "\n";  
print_r ($conn->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

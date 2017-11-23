---
title: "PDO::ErrorCode | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3342ebf997f8cd915efe939ead8baa5e868eb0f2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
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
  
## <a name="remarks"></a>Замечания  
Для некоторых успешных операций PDO::errorCode в драйвере PDO_SQLSRV возвращает предупреждения. Например, для успешного подключения PDO::errorCode возвращает значение "01000", указывающее SQL_SUCCESS_WITH_INFO.  
  
PDO::errorCode возвращает только сведения об ошибках для операций, выполненных непосредственно для подключения к базе данных. Если вы создаете экземпляр PDOStatement через PDO::prepare или PDO::query и выдаете ошибку для объекта инструкции, PDO::errorCode не получает эту ошибку. Необходимо вызвать метод PDOStatement::errorCode, чтобы возвратить код ошибки для операции, выполненной с определенным объектом инструкции.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
В этом примере неправильно указано имя столбца (`Cityx` вместо `City`), что вызывает ошибку, которой затем сообщается.  
  
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
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

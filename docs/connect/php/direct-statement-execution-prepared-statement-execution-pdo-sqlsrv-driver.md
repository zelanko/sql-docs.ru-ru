---
title: Прямой - подготовленной драйвер PDO_SQLSRV для выполнения инструкции инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c721a32936bf39d91042d6b7ac89a03a5fd85d6
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2018
ms.locfileid: "42784624"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этой статье описывается использование атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY для указания прямого выполнения инструкции вместо используемого по умолчанию, которое заключается в выполнении подготовленной инструкции. С помощью подготовленной инструкции может привести к более высокую производительность, если инструкция выполняется более одного раза при помощи привязки параметра.  
  
## <a name="remarks"></a>Remarks  
Если вы хотите отправить [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции непосредственно на сервер без Подготовка инструкции с помощью драйвера, можно задать с помощью атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY [PDO::setAttribute](../../connect/php/pdo-setattribute.md) (или при передаче driver-параметр [PDO::__construct](../../connect/php/pdo-construct.md)) или при вызове [PDO::prepare](../../connect/php/pdo-prepare.md). По умолчанию, PDO::SQLSRV_ATTR_DIRECT_QUERY значение False (в выполнении подготовленной инструкции use).  
  
Если вы используете [PDO::query](../../connect/php/pdo-query.md), может потребоваться прямое выполнение. Перед вызовом [PDO::query](../../connect/php/pdo-query.md), вызовите [PDO::setAttribute](../../connect/php/pdo-setattribute.md) и присвоено значение True, PDO::SQLSRV_ATTR_DIRECT_QUERY.  Каждый вызов [PDO::query](../../connect/php/pdo-query.md) могут выполняться с другими параметрами для PDO::SQLSRV_ATTR_DIRECT_QUERY.  
  
Если вы используете [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md) для выполнения запроса несколько раз с помощью связанных параметров, на выполнение подготовленной инструкции оптимизирует выполнение повторяющихся запросов.  В этом случае вызов [PDO::prepare](../../connect/php/pdo-prepare.md) с PDO::SQLSRV_ATTR_DIRECT_QUERY, значение False в параметре массива параметров драйвера. При необходимости вы можете выполнить подготовленные инструкции с PDO::SQLSRV_ATTR_DIRECT_QUERY равным False.  
  
После вызова метода [PDO::prepare](../../connect/php/pdo-prepare.md), PDO::SQLSRV_ATTR_DIRECT_QUERY значение нельзя изменить при выполнении подготовленного запроса.  
  
Если запрос требует контекста, который был задан в предыдущем запросе, затем выполните запросы PDO::SQLSRV_ATTR_DIRECT_QUERY задается значение True. Например при использовании временных таблиц в запросы, PDO::SQLSRV_ATTR_DIRECT_QUERY должно быть присвоено значение True.  
  
В следующем примере показано, что если требуется контекст от предыдущей инструкции, необходимо задать PDO::SQLSRV_ATTR_DIRECT_QUERY значение True.  В этом примере используется временные таблицы, которые доступны только на последующие инструкции в программе, если запросы выполняются непосредственно.  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

---
title: Direct — подготовленная инструкция для выполнения инструкции PDO_SQLSRV Driver | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa9e544fb7b79009d86a5742946a722d5adc18f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993617"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этой статье описывается использование атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY для указания прямого выполнения инструкции вместо используемого по умолчанию, которое заключается в выполнении подготовленной инструкции. Использование подготовленной инструкции может привести к лучшей производительности, если инструкция выполняется более одного раза с помощью привязки параметров.  
  
## <a name="remarks"></a>Remarks  
Если требуется отправить [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию непосредственно на сервер без подготовки инструкции драйвером, можно задать атрибут PDO:: SQLSRV_ATTR_DIRECT_QUERY с [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) (или в качестве параметра драйвера, переданного [PDO:: __construct ](../../connect/php/pdo-construct.md)) или при вызове [PDO::p готовка](../../connect/php/pdo-prepare.md). По умолчанию параметр PDO:: SQLSRV_ATTR_DIRECT_QUERY имеет значение false (используется выполнение подготовленной инструкции).  
  
При использовании [PDO:: Query](../../connect/php/pdo-query.md)может потребоваться прямое выполнение. Перед вызовом [PDO:: Query](../../connect/php/pdo-query.md)вызовите [PDO:: SETATTRIBUTE](../../connect/php/pdo-setattribute.md) и задайте PDO:: SQLSRV_ATTR_DIRECT_QUERY в true.  Каждый вызов [PDO:: Query](../../connect/php/pdo-query.md) можно выполнить с другим параметром PDO:: SQLSRV_ATTR_DIRECT_QUERY.  
  
При использовании [PDO::p готовка](../../connect/php/pdo-prepare.md) и [PDOStatement:: Execute](../../connect/php/pdostatement-execute.md) для многократного выполнения запроса с использованием привязанных параметров выполнение подготовленной инструкции оптимизирует выполнение повторяющегося запроса.  В этом случае вызовите [PDO::p готовка](../../connect/php/pdo-prepare.md) с PDO:: SQLSRV_ATTR_DIRECT_QUERY, указав значение false в параметре массива параметров драйвера. При необходимости можно выполнять подготовленные инструкции с параметром PDO:: SQLSRV_ATTR_DIRECT_QUERY, имеющим значение false.  
  
После вызова [PDO::p готовка](../../connect/php/pdo-prepare.md)значение PDO:: SQLSRV_ATTR_DIRECT_QUERY не может измениться при выполнении подготовленного запроса.  
  
Если запросу требуется контекст, заданный в предыдущем запросе, выполните запросы с параметром PDO:: SQLSRV_ATTR_DIRECT_QUERY, имеющим значение true. Например, если в запросах используются временные таблицы, PDO:: SQLSRV_ATTR_DIRECT_QUERY должно иметь значение true.  
  
В следующем примере показано, что если требуется контекст из предыдущей инструкции, необходимо установить PDO:: SQLSRV_ATTR_DIRECT_QUERY в значение true. В этом образце используются временные таблицы, которые доступны только в последующих инструкциях в программе при выполнении запросов напрямую.  
  
> [!NOTE]
> Если запрос вызывает хранимую процедуру, а в этой хранимой процедуре используются временные таблицы, используйте [PDO:: Exec](../../connect/php/pdo-exec.md) .

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
[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

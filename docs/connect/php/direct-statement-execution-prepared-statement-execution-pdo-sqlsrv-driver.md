---
title: Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV | Документация Майкрософт
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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993617"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdo_sqlsrv-driver"></a>Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этой статье описывается использование атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY для указания прямого выполнения инструкции вместо используемого по умолчанию, которое заключается в выполнении подготовленной инструкции. Использование подготовленной инструкции может привести к лучшей производительности, если инструкция выполняется более одного раза с помощью привязки параметров.  
  
## <a name="remarks"></a>Remarks  
Если требуется отправить инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] непосредственно на сервер без подготовки инструкции драйвером, можно задать атрибут PDO::SQLSRV_ATTR_DIRECT_QUERY с [PDO::setAttribute](../../connect/php/pdo-setattribute.md) (или в качестве параметра драйвера, переданного к [PDO::__construct](../../connect/php/pdo-construct.md)), или при вызове [PDO::prepare](../../connect/php/pdo-prepare.md). По умолчанию параметр PDO::SQLSRV_ATTR_DIRECT_QUERY имеет значение false (используйте выполнение подготовленной инструкции).  
  
При использовании [PDO::query](../../connect/php/pdo-query.md) может потребоваться прямое выполнение. Перед вызовом [PDO::query](../../connect/php/pdo-query.md) вызовите [PDO::setAttribute](../../connect/php/pdo-setattribute.md) и задайте для PDO:: PDO::SQLSRV_ATTR_DIRECT_QUERY значение true.  Каждый вызов [PDO::query](../../connect/php/pdo-query.md) может быть выполнен с другим параметром для PDO::SQLSRV_ATTR_DIRECT_QUERY.  
  
При использовании [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md) для многократного выполнения запроса с использованием привязанных параметров выполнение подготовленной инструкции оптимизирует выполнение повторяющегося запроса.  В этом случае вызовите параметр [PDO::prepare](../../connect/php/pdo-prepare.md) с PDO::SQLSRV_ATTR_DIRECT_QUERY со значением false в параметре массива параметров драйвера. При необходимости можно выполнять подготовленные инструкции с параметром PDO::SQLSRV_ATTR_DIRECT_QUERY, имеющим значение false.  
  
После вызова [PDO::prepare](../../connect/php/pdo-prepare.md) значение PDO::SQLSRV_ATTR_DIRECT_QUERY не может измениться при выполнении подготовленного запроса.  
  
Если запросу требуется контекст, заданный в предыдущем запросе, выполните запросы с помощью параметра PDO::SQLSRV_ATTR_DIRECT_QUERY и установите значение True. Например, если в запросах используются временные таблицы, параметр PDO::SQLSRV_ATTR_DIRECT_QUERY должен иметь значение True.  
  
В следующем примере показано, что если требуется контекст из предыдущей инструкции, для параметра PDO::SQLSRV_ATTR_DIRECT_QUERY необходимо задать значение True. В этом образце используются временные таблицы, которые доступны только в последующих инструкциях в программе при выполнении запросов напрямую.  
  
> [!NOTE]
> Если запрос должен вызвать хранимую процедуру и в этой хранимой процедуре используются временные таблицы, используйте вместо этого [PDO::exec](../../connect/php/pdo-exec.md).

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
  

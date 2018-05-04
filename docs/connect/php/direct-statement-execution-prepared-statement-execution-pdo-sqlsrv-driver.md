---
title: Прямой - подготовленной инструкции драйвер PDO_SQLSRV выполнение инструкции | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaa67ec16086dcfac895422c58c8cdddc50ef243
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этом разделе описывается использование атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY для указания выполнения прямой инструкции вместо значения по умолчанию, который находится на выполнение подготовленной инструкции. С помощью подготовленных инструкций может привести к более высокую производительность при выполнении инструкции несколько раз с помощью параметра привязки.  
  
## <a name="remarks"></a>Замечания  
Если вы хотите отправить [!INCLUDE[tsql](../../includes/tsql_md.md)] инструкции непосредственно на сервер без Подготовка инструкции с помощью драйвера, можно задать с помощью атрибута PDO::SQLSRV_ATTR_DIRECT_QUERY [PDO::setAttribute](../../connect/php/pdo-setattribute.md) (или как driver-параметр, передаваемый в [PDO::__construct](../../connect/php/pdo-construct.md)) или при вызове [PDO::prepare](../../connect/php/pdo-prepare.md). По умолчанию значение PDO::SQLSRV_ATTR_DIRECT_QUERY равно False (на выполнение подготовленной инструкции use).  
  
Если вы используете [PDO::query](../../connect/php/pdo-query.md), может потребоваться прямое выполнение. Перед вызовом метода [PDO::query](../../connect/php/pdo-query.md), вызовите [PDO::setAttribute](../../connect/php/pdo-setattribute.md) и PDO::SQLSRV_ATTR_DIRECT_QUERY присвоено значение True.  Каждый вызов [PDO::query](../../connect/php/pdo-query.md) могут быть выполнены с другими параметрами для PDO::SQLSRV_ATTR_DIRECT_QUERY.  
  
Если вы используете [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md) для многократного выполнения запроса с помощью привязанные параметры, на выполнение подготовленной инструкции оптимизирует выполнение повторяющихся запросов.  В этом случае вызов [PDO::prepare](../../connect/php/pdo-prepare.md) с PDO::SQLSRV_ATTR_DIRECT_QUERY значение False в параметре массива параметров драйвера. При необходимости можно выполнять подготовленных инструкций с PDO::SQLSRV_ATTR_DIRECT_QUERY равным False.  
  
После вызова метода [PDO::prepare](../../connect/php/pdo-prepare.md), PDO::SQLSRV_ATTR_DIRECT_QUERY значение нельзя изменить при выполнении подготовленного запроса.  
  
Если запрос требует контекст, который был задан в предыдущем запросе, затем выполните запросы с PDO::SQLSRV_ATTR_DIRECT_QUERY имеет значение True. Например при использовании временных таблиц в запросах, PDO::SQLSRV_ATTR_DIRECT_QUERY должно быть присвоено значение True.  
  
В следующем примере показано, что при необходимости контекста из предыдущей инструкции необходимо задать значение True, PDO::SQLSRV_ATTR_DIRECT_QUERY.  Этот пример использует временные таблицы, которые доступны только для последующих инструкций в программе запросы выполняются непосредственно.  
  
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
  
## <a name="see-also"></a>См. также  
[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

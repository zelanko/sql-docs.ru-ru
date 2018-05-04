---
title: sqlsrv_has_rows | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
helpviewer_keywords:
- API Reference, sqlsrv_has_rows
- sqlsrv_has_rows
ms.assetid: 4da7f640-cf12-409f-9e00-95b30a8d5e17
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 153d221f6fdf3ac81c831b23e95e7bc87365b7bf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvhasrows"></a>sqlsrv_has_rows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Указывает, имеет ли результирующий набор одну или несколько строк.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_has_rows( resource $stmt )  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: выполненная инструкция.  
  
## <a name="return-value"></a>Возвращаемое значение  
Если в результирующем наборе есть строки, возвращается значение **true**. Если строки отсутствуют или происходит сбой вызова функции возвращается значение **false**.  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $server = "server_name";  
   $conn = sqlsrv_connect( $server, array( 'Database' => 'Northwind' ) );  
  
   $stmt = sqlsrv_query( $conn, "select * from orders where CustomerID = 'VINET'" , array());  
  
   if ($stmt !== NULL) {  
      $rows = sqlsrv_has_rows( $stmt );  
  
      if ($rows === true)  
         echo "\nthere are rows\n";  
      else   
         echo "\nno rows\n";  
   }  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

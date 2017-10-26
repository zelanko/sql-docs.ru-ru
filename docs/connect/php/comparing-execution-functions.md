---
title: "Сравнение функций выполнения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e74c7433ab2e3a831d6aa800a2a1a9abbbda5863
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-execution-functions"></a>Сравнение функций выполнения
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Предоставляет [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] несколько вариантов для выполнения функций.  
  
При использовании драйвера SQLSRV используйте [sqlsrv_query](../../connect/php/sqlsrv-query.md) для выполнения одного запроса и [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) с [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) для многократного выполнения подготовленной инструкции с различными значениями параметров при каждом выполнении.  
  
При использовании драйвера PDO_SQLSRV запрос можно выполнить одним из следующих способов:  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
  


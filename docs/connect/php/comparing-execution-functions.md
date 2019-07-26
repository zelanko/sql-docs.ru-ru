---
title: Сравнение функций выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2b4d6c85c399589aae4eedbaade4bbdc4f70609
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993740"
---
# <a name="comparing-execution-functions"></a>Сравнение функций выполнения
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Предоставляет [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] несколько вариантов для выполнения функций.  

## <a name="sqlsrv-execution-functions"></a>Функции выполнения SQLSRV  
При использовании драйвера SQLSRV используйте [sqlsrv_query](../../connect/php/sqlsrv-query.md) для выполнения одного запроса и [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) с [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) для многократного выполнения подготовленной инструкции с различными значениями параметров при каждом выполнении.  

## <a name="pdosqlsrv-execution-functions"></a>Функции выполнения PDO_SQLSRV 
При использовании драйвера PDO_SQLSRV запрос можно выполнить одним из следующих способов:  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по драйверу PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

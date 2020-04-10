---
title: PDO::quote | Документация Майкрософт
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db661eea0ea4b3b46e3a73f7e1f4609267bbae41
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919062"
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Обрабатывает строку для использования в запросе, заключая входную строку в кавычки, как того требует основная база данных SQL Server. PDO::quote будет экранировать специальные символы во входной строке с помощью стиля кавычек, подходящего для SQL Server.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Параметры  
$*string*: строка для заключения в кавычки.  
  
$*parameter_type*: необязательный символ (целое число), указывающий тип данных.  Значение по умолчанию — PDO::PARAM_STR.  

Новые константы PDO появились в PHP 7.2 для поддержки [сопоставления строк в Юникоде и других кодировках](https://wiki.php.net/rfc/extended-string-types-for-pdo). Строки Юникода можно заключить в кавычки с префиксом N (например, N'string' вместо 'string').

1. PDO::P ARAM_STR_NATL — это новый тип для строк Юникода, который применяется в операции побитового ИЛИ со значением PDO::PARAM_STR
1. PDO::P ARAM_STR_CHAR — это новый тип для строк, отличных от Юникода, который применяется в операции побитового ИЛИ со значением PDO::PARAM_STR
1. PDO::ATTR_DEFAULT_STR_PARAM — задайте значение PDO::PARAM_STR_NATL или PDO::PARAM_STR_CHAR, чтобы задать значение по умолчанию для операции побитового ИЛИ со значением PDO::PARAM_STR

Начиная с версии 5.8.0 эти константы можно использовать с PDO::quote.
  
## <a name="return-value"></a>Возвращаемое значение  
Строка в кавычках, которую можно передать в инструкцию SQL, или значение false в случае ошибки.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="example"></a>Пример  

Следующий скрипт демонстрирует, как расширенные строковые типы влияют на работу PDO::quote () в PHP версии 7.2 и более поздних.

```
<?php
$database = "test";
$server = "(local)";
$db = new PDO("sqlsrv:server=$server; Database=$database", "", "");

$db->quote('über', PDO::PARAM_STR | PDO::PARAM_STR_NATL); // N'über'
$db->quote('foo'); // 'foo'

$db->setAttribute(PDO::ATTR_DEFAULT_STR_PARAM, PDO::PARAM_STR_NATL);
$db->quote('über'); // N'über'
$db->quote('foo', PDO::PARAM_STR | PDO::PARAM_STR_CHAR); // 'foo'
?>
```
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

---
title: PDO::__construct
description: Справочник по API для функции PDO::__construct в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ee53aff-6fe4-44cd-a15b-51770c98c712
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a815f72ef466442c601d0720243f9476a0cfc95
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081673"
---
# <a name="pdo__construct"></a>PDO::__construct
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Устанавливает соединение с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PDO::__construct($dsn [,$username [,$password [,$driver_options ]]] )  
```  
  
#### <a name="parameters"></a>Параметры  
*$dsn*: : строка, содержащая имя префикса (всегда `sqlsrv`), двоеточие и ключевое слово Server. Например, `"sqlsrv:server=(local)"`. При необходимости можно другие ключевые слова подключения. Описание ключевого слова Server и других ключевых слов подключения см. в статье [Connection Options](../../connect/php/connection-options.md) . Вся *$dsn* берется в кавычки, поэтому каждое ключевое слово подключения заключать в отдельные кавычки не нужно.  
  
*$username.* Необязательный параметр. Строка, содержащая имя пользователя. Для подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите имя пользователя. Для подключения с использованием проверки подлинности Windows укажите `""`.  
  
*$password*: необязательно. Строка, содержащая пароль пользователя. Для подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите пароль. Для подключения с использованием проверки подлинности Windows укажите `""`.  
  
*$driver_options.* Необязательный параметр. Вы можете указать атрибуты диспетчера драйверов PDO и эксклюзивные атрибуты драйвера [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]: PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ATTR_DIRECT_QUERY. Недопустимый атрибут не вызывает исключение. Недопустимые атрибуты вызывают исключения при указании [PDO::setAttribute](../../connect/php/pdo-setattribute.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает объект PDO. В случае сбоя возвращает объект PDOException.  
  
## <a name="exceptions"></a>Исключения  
PDOException  
  
## <a name="remarks"></a>Remarks  
Объект соединения можно закрыть, установив для экземпляра значение NULL.  
  
После подключения PDO::errorCode отображает 01000 вместо 00000.  
  
Если PDO::__construct по какой-то причине не срабатывает, выдается исключение, даже если для PDO::ATTR_ERRMODE задано значение PDO::ERRMODE_SILENT.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example-with-database"></a>Пример с базой данных  
Этот пример показывает, как подключиться к серверу с использованием проверки подлинности Windows, и указать базу данных.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:Server=(local) ; Database = AdventureWorks ", "", "", array(PDO::SQLSRV_ATTR_DIRECT_QUERY => true));   
  
   $query = 'SELECT * FROM Person.ContactType';   
   $stmt = $c->query( $query );   
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ) {   
      print_r( $row );   
   }  
   $c = null;   
?>  
```  
  
## <a name="example-without-database"></a>Пример без базы данных  
Этот пример показывает, как подключиться к серверу, указав базу данных позднее.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec( "USE AdventureWorks");  
   $query = 'SELECT * FROM Person.ContactType';  
   $stmt = $c->query( $query );  
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
      print_r( $row );  
   }  
   $c = null;  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

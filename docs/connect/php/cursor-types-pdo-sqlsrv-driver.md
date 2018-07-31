---
title: Типы курсоров (драйвер PDO_SQLSRV) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72cf83b4c4903c7df0b6a857746937e848fccf80
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062361"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>Типы курсоров (драйвер PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер PDO_SQLSRV предоставляет возможность создавать прокручиваемые результирующие наборы с одним из нескольких курсоров.  
  
Сведения о том, как для указания курсора с помощью драйвера PDO_SQLSRV и примеры кода, см. в разделе [PDO::prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV и серверных курсоров  
До версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], позволял создавать результирующий набор с курсором последовательного или статических серверных драйвера PDO_SQLSRV. Начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], также доступны управляемые набором ключей и динамические курсоры.  
  
Можно указать тип курсора на стороне сервера с помощью PDO::prepare или PDOStatement::setAttribute, чтобы выбрать любой из этих типов курсоров:  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_FWDONLY  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_SCROLL  
  
Вы можете запросить курсор keyset или dynamic, указав PDO::ATTR_CURSOR = > PDO::CURSOR_SCROLL и затем передать соответствующее значение для PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Ниже приведены возможные значения, которые можно передать PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV и курсоры на стороне клиента  
Клиентские курсоры были добавлены в версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , позволяет кэшировать весь результирующий набор в памяти. Одним из преимуществ является то, что количество строк доступен после выполнения запроса.  
  
Клиентские курсоры следует использовать для малых средних результирующих наборов. Больших результирующих наборов следует использовать курсоры на стороне сервера.  
  
Запрос будет возвращать значение false, если буфер недостаточно велик для хранения весь результирующий набор при использовании клиентского курсора. Можно увеличить размер буфера, вплоть до предела памяти PHP.  
  
Можно настроить размер буфера, который содержит результирующий набор с помощью атрибута PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE [PDO::setAttribute](../../connect/php/pdo-setattribute.md) или [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md). Можно также задать максимальный размер буфера в файле php.ini с pdo_sqlsrv.client_buffer_max_kb_size (например, pdo_sqlsrv.client_buffer_max_kb_size = 1024).  
  
Вы указываете, что клиентский курсор с помощью PDO::prepare или PDOStatement::setAttribute и выберите PDO::ATTR_CURSOR = > PDO::CURSOR_SCROLL тип курсора.  Затем укажите PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE = > PDO::SQLSRV_CURSOR_BUFFERED.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  

---
title: Типы курсоров (драйвер PDO_SQLSRV)
description: Сведения о различных курсорах на стороне сервера и клиента, а также о том, как пользователи могут указать тип курсора при использовании драйвера Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7660f71ba8a288840210734b85ac551a0770fc81
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680589"
---
# <a name="cursor-types-pdo_sqlsrv-driver"></a>Типы курсоров (драйвер PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер PDO_SQLSRV позволяет создавать прокручиваемые результаты с помощью одного из нескольких курсоров.

Сведения об указании курсоров для драйвера PDO_SQLSRV и примеры кода вы найдете в описании [PDO::prepare](../../connect/php/pdo-prepare.md).

## <a name="pdo_sqlsrv-and-server-side-cursors"></a>PDO_SQLSRV и курсоры на стороне сервера
До выхода [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии 3.0 драйвер PDO_SQLSRV позволял использовать для получения результатов только последовательный или статический курсор на стороне сервера. Начиная с [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии 3.0, стали доступны наборы ключей и динамические курсоры.

Тип курсора на стороне сервера вы можете указать с помощью [PDO::prepare](../../connect/php/pdo-prepare.md) из следующего списка типов:

-   `PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY`

-   `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`

Чтобы запросить динамический, статический курсор или курсор с набором ключей, укажите `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` и передайте соответствующее значение в `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE`. Для курсоров на стороне сервера в `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` можно передать следующие значения:

-   `PDO::SQLSRV_CURSOR_DYNAMIC`

-   `PDO::SQLSRV_CURSOR_STATIC`

-   `PDO::SQLSRV_CURSOR_KEYSET`

## <a name="pdo_sqlsrv-and-client-side-cursors"></a>PDO_SQLSRV и курсоры на стороне клиента
Курсоры на стороне клиента были добавлены в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии 3.0. Они позволяют кэшировать в памяти весь результирующий набор. Одним из их преимуществ является то, что после выполнения запроса доступно количество строк.

Курсоры на стороне клиента следует использовать только для малых и средних результирующих наборов. Для больших результирующих наборов следует использовать курсоры на стороне сервера.

При использовании курсора на стороне клиента запрос будет возвращать значение false, если буфер недостаточно велик для хранения полного результирующего набора. Вы можете увеличить размер этого буфера вплоть до максимального объема памяти PHP.

Размер буфера для результирующего набора можно увеличить с помощью атрибута `PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE` в [PDO::setAttribute](../../connect/php/pdo-setattribute.md) или [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md). Также максимальный размер буфера можно задать в файле php.ini параметром pdo_sqlsrv.client_buffer_max_kb_size (например, pdo_sqlsrv.client_buffer_max_kb_size = 1024).

Вы можете запросить курсор на стороне клиента с помощью [PDO::prepare](../../connect/php/pdo-prepare.md), указав тип курсора `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`, а затем указать `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED`.

## <a name="example"></a>Пример
В следующем примере показано, как указать буферизованный курсор.
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


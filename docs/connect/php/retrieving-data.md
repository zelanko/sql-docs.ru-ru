---
title: Получение данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3414992c-61c0-4e7d-b509-72517e52c1bb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6ac8e52e46108e88693a96d587e3af2b79e4ff4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833112"
---
# <a name="retrieving-data"></a>Извлечение данных
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья и статьи в данном разделе посвящены извлечению данных.  
  
## <a name="sqlsrv-driver"></a>Драйвер SQLSRV  
Драйвер SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] предоставляет следующие возможности для извлечения данных из результирующего набора:  
  
-   [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)  
  
-   [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)  
  
-   [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)/[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)  
  
> [!NOTE]  
> При использовании любых из упомянутых выше функций, избегайте использования сравнений со значением NULL в качестве критерия для выхода из циклов. Поскольку функции **sqlsrv** возвращают значение false, когда происходит ошибка, следующий код может привести к бесконечному циклу при возникновении ошибки в [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md):  
>   
> `/*``This code could result in an infinite loop. It is recommended that`  
>   
> `you do NOT use null comparisons as the criterion for exiting loops,`  
>   
> `as is done here. */`  
>   
> `do{`  
>   
> `$result = sqlsrv_fetch_array($stmt);`  
>   
> `} while( !is_null($result));`  
  
Если запрос извлекает больше одного результирующего набора, можно перейти к следующему результирующему набору с помощью [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md).  
  
Начиная с версии 1.1 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] можно использовать [sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md), чтобы определить наличие строк в результирующем наборе.  
  
## <a name="pdosqlsrv-driver"></a>Драйвер PDO_SQLSRV  
Драйвер PDO_SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] предоставляет следующие возможности для извлечения данных из результирующего набора:  
  
-   [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md)  
  
-   [PDOStatement::fetchAll](../../connect/php/pdostatement-fetchall.md)  
  
-   [PDOStatement::fetchColumn](../../connect/php/pdostatement-fetchcolumn.md)  
  
-   [PDOStatement::fetchObject](../../connect/php/pdostatement-fetchobject.md)  
  
Если запрос извлекает больше одного результирующего набора, можно перейти к следующему результирующему набору с помощью [PDOStatement::nextRowset](../../connect/php/pdostatement-nextrowset.md).  
  
Можно узнать, сколько строк содержит результирующий набор, если задать прокручиваемый курсор, а затем вызвать [PDOStatement::rowCount](../../connect/php/pdostatement-rowcount.md).  
  
[PDO::prepare](../../connect/php/pdo-prepare.md) позволяет указать тип курсора. Затем с помощью [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) можно выбрать строку. Дополнительные сведения и пример см. в статье [PDO::prepare](../../connect/php/pdo-prepare.md) .  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
|[Извлечение данных в виде потока](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)|Содержит общие сведения о потоковой передаче данных с сервера, а также ссылки на конкретные варианты использования.|  
|[Использование параметров направления](../../connect/php/using-directional-parameters.md)|Описывает, как использовать параметры направления при вызове хранимой процедуры.|  
|[Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)|Демонстрирует, как создать результирующий набор со строками, доступ к которым можно осуществлять в любом порядке, при использовании драйвера SQLSRV.|  
|[Практическое руководство. Получение типа даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)|Описывает процедуру извлечения типов даты и времени в виде строк.|  
  
## <a name="related-sections"></a>См. также  
[Практическое руководство. Указание типов данных PHP](../../connect/php/how-to-specify-php-data-types.md)  
  
## <a name="see-also"></a>См. также:  
[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Извлечение данных](../../connect/php/retrieving-data.md)  
  

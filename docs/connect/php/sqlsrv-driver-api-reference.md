---
title: "Справочник по API для драйвера SQLSRV | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2bd1cf731f49119e54fb9e5a548a8988af1ef9fc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrv-driver-api-reference"></a>Справочник по API для драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

API для драйвера SQLSRV в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] имеет имя **sqlsrv**. Все **sqlsrv** функции начинаются с **sqlsrv_** после которого следует глагол или существительное. Функции с глаголом выполняют определенное действие, а функции с существительным возвращают определенные виды метаданных.  
  
## <a name="in-this-section"></a>В этом разделе  
Драйвер SQLSRV содержит следующие функции:  
  
|Функция|Description|  
|------------|---------------|  
|[sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)|Начинает транзакцию.|  
|[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)|Отменяет инструкцию, удаляет все ожидающие результаты для инструкции.|  
|[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)|Предоставляет сведения о клиенте.|  
|[sqlsrv_close](../../connect/php/sqlsrv-close.md)|Закрывает соединение. Освобождает все ресурсы, связанные с соединением.|  
|[sqlsrv_commit](../../connect/php/sqlsrv-commit.md)|Фиксирует транзакцию.|  
|[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)|Изменяет конфигурации обработки ошибок и ведения журнала.|  
|[sqlsrv_connect](../../connect/php/sqlsrv-connect.md)|Создает и открывает соединение.|  
|[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)|Возвращает сведения об ошибке и (или) предупреждении для последней операции.|  
|[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)|Выполняет подготовленную инструкцию.|  
|[sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)|Делает следующую строку данных доступной для чтения.|  
|[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)|Извлекает следующую строку данных в виде массива с числовым индексом и (или) ассоциативного массива.|  
|[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)|Извлекает следующую строку в качестве объекта.|  
|[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)|Возвращает метаданные поля.|  
|[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)|Закрывает инструкцию. Освобождает все ресурсы, связанные с инструкцией.|  
|[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)|Возвращает значение указанного параметра конфигурации.|  
|[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)|Извлекает поле в текущей строке по индексу. Можно указать тип возвращаемого значения PHP.|  
|[sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md)|Определяет, имеет ли результирующий набор одну или несколько строк.|  
|[sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md)|Делает следующий результат доступным для обработки.|  
|[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)|Сообщает число строк в результирующем наборе.|  
|[sqlsrv_num_fields](../../connect/php/sqlsrv-num-fields.md)|Извлекает количество полей в активном результирующем наборе.|  
|[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)|Подготавливает запрос Transact-SQL без его выполнения. Выполняет неявную привязку параметров.|  
|[sqlsrv_query](../../connect/php/sqlsrv-query.md)|Подготавливает и выполняет запрос Transact-SQL.|  
|[sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)|Выполняет откат транзакции.|  
|[sqlsrv_rows_affected](../../connect/php/sqlsrv-rows-affected.md)|Возвращает количество измененных строк.|  
|[sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)|Отправляет до 8 килобайт (8 КБ) данных на сервер с каждым вызовом функции.|  
|[sqlsrv_server_info](../../connect/php/sqlsrv-server-info.md)|Предоставляет сведения о сервере.|  
  
## <a name="reference"></a>Справочник  
[Руководство по PHP](http://go.microsoft.com/fwlink/?LinkId=105500)  
  
## <a name="see-also"></a>См. также:  
[Общие сведения о драйвере PHP SQL](../../connect/php/overview-of-the-php-sql-driver.md)
[константы &#40; Драйверы Майкрософт для PHP для SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Приступая к работе с драйвером SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
  


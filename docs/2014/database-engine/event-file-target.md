---
title: Целевой файл событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- event file target
- file target [SQL Server extended events]
- targets [SQL Server extended events], file target
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d60253eafa67b7d7922da6890a8dbb6fbe3536a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203914"
---
# <a name="event-file-target"></a>Event File Target
  Цель «Файл событий» — это цель, осуществляющая запись всех буферов на диск.  
  
 В следующей таблице описаны доступные параметры для настройки цели «Файл событий».  
  
|Параметр|Допустимые значения|Описание|  
|------------|--------------------|-----------------|  
|filename|Любая строка длиной до 260 символов. Это значение обязательно.|Расположение и имя файла.<br /><br /> Можно использовать любое расширение имени файла.|  
|max_file_size|Любое 64-разрядное целое число. Это значение является необязательным.|Верхний предел размера файла в мегабайтах (МБ). Если аргумент max_file_size не указан, файл будет увеличиваться до исчерпания пространства на диске. Размер файла по умолчанию составляет 1 ГБ.<br /><br /> Аргумент max_file_size должен быть больше по сравнению с текущим размером буфера сеанса. Иначе целевой файл нельзя будет инициализировать и появится сообщение о недопустимости значения параметра max_file_size. Текущий размер буферов можно получить запросом к столбцу buffer_size в динамическом административном представлении [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) .<br /><br /> Если размер файла по умолчанию меньше размера буфера сеанса, рекомендуется задать для max_file_size значение, указанное в столбце max_memory представления каталога [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .<br /><br /> Если значение параметра max_file_size больше размера буферов сеанса, его можно округлить до ближайшей меньшей величины, кратной размеру буфера сеанса. Созданный в результате целевой файл по размеру может быть меньше заданной величины max_file_size. Например, если размер буфера составляет 100 МБ, а max_file_size равен 150 МБ, размер результирующего файла округляется до меньшего значения 100 МБ, поскольку второй буфер не уместится в оставшихся 50 МБ.<br /><br /> Если размер файла по умолчанию меньше размера буфера сеанса, рекомендуется задать для max_file_size значение, указанное в столбце max_memory представления каталога [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .|  
|max_rollover_files|Любое 32-разрядное целое число. Это значение является необязательным.|Максимальное число файлов, хранимых в файловой системе. Значение по умолчанию — 5.|  
|increment|Любое 32-разрядное целое число. Это значение является необязательным.|Шаг увеличения размера файла в мегабайтах (МБ). Если не указан, то значением по умолчанию будет двойной размер буфера сеанса.|  
  
 При первом создании цели "Файл событий" к заданному имени файла присоединяется _0\_ и длинное целое число. Это длинное целое число вычисляется как количество миллисекунд, прошедших с 1 января 1600 года до момента создания файла. Последующие файлы продолжения используют тот же формат. Сравнив значения длинных целых, можно определить самый последний файл. В следующем примере показано, как происходит именование файлов в случае, если в качестве имени файла указано «C:\OutputFiles\MyOutput.xel»:  
  
-   первый созданный файл — C:\OutputFiles\MyOutput_0_128500310259380000.xel  
  
-   первый файл продолжения — C:\OutputFiles\MyOutput_0_128505831770890000.xel  
  
-   второй файл продолжения — C:\OutputFiles\MyOutput_0_132410772966237000.xel  
  
## <a name="adding-the-target-to-a-session"></a>Добавление цели к сеансу  
 Для добавления целевого файла событий в сеанс расширенных событий следует использовать следующую инструкцию при создании или изменении сеанса события, заменив *имя_файла* нужным именем файла и его расположением.  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## <a name="reviewing-the-target-output"></a>Просмотр целевого вывода  
 Для просмотра результата цели "Файл" следует использовать функцию sys.fn_xe_file_target_read_file function. Рекомендуется представлять данные в виде XML. Можно использовать следующий синтаксис, заменив *имя_файла* именем файла и его расположением, указанными при добавлении цели.  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## <a name="see-also"></a>См. также  
 [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)   
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  

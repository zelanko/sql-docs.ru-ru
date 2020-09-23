---
title: Коды возврата (драйвер OLE DB)
description: Узнайте о кодах возврата для функций OLE DB Driver for SQL Server и о том, как получить дополнительные сведения о результатах, помимо данных об успешном выполнении.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18d2b3f5029e70379f0692a919aa8fe6cd4ed10b
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862246"
---
# <a name="return-codes"></a>Коды возврата
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в статье [Коды возврата (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Если функция-член OLE DB Driver for SQL Server возвращает S_OK, значит выполнение функции завершилось успешно.  
  
 Если функция-член драйвера OLE DB для SQL Server возвращает не S_OK, с помощью макросов OLE/COM FAILED и IS_ERROR можно получить из возвращенного функцией значения HRESULT информацию об успешном или неуспешном выполнении функции.  
  
 Если макрос FAILED или IS_ERROR вернул значение TRUE, это служит сигналом для драйвера OLE DB для SQL Server, что выполнение функции было неуспешным. Если FAILED или IS_ERROR имеет значение FALSE, а HRESULT не равно S_OK, значит OLE DB Driver for SQL Server извещает потребителя о частично успешном выполнении функции. Потребитель может получить подробные сведения об этом "успехе с оговорками" через интерфейсы для работы с ошибками, предоставляемые драйвером OLE DB для SQL Server. Через эти же интерфейсы драйвера OLE DB для SQL Server можно получить подробные сведения в случае, когда вызов функции был явно неудачным (макрос FAILED возвращает значение TRUE).  
  
 Среди разных вариантов "успеха с оговорками" потребители OLE DB Driver for SQL Server чаще всего получают в параметре HRESULT значение DB_S_ERRORSOCCURRED. Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 Функции-члены OLE DB Driver for SQL Server не возвращают код успеха S_FALSE. Все функции-члены OLE DB Driver for SQL Server обозначают успешное выполнение только кодом успеха S_OK.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  

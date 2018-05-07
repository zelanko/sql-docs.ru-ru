---
title: Коды возврата | Документы Microsoft
description: 'Коды возврата '
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 18564da5e47a6b28b92841163847bfd0b8a28aa0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="return-codes"></a>Коды возврата
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в разделе [коды возврата (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Если драйвер OLE DB для SQL Server функция-член возвращает значение S_OK, функция выполнена успешно.  
  
 Если драйвер OLE DB для SQL Server функции-члена не возвращает значение S_OK, макросы распаковки HRESULT OLE/COM FAILED и IS_ERROR можно определить общий успех или сбой функции.  
  
 Если макрос FAILED или IS_ERROR возвращает значение TRUE, драйвер OLE DB для SQL Server потребитель может быть уверен аварийное завершение выполнения функции. Когда FAILED или IS_ERROR вернул значение FALSE, а значение HRESULT не равно S_OK, драйвер OLE DB для SQL Server, это означает функции был успешным в некотором смысле. Потребитель может получить подробные сведения об этой «успеха с оговорками» возврат из драйвер OLE DB для SQL Server ошибки интерфейсов. Кроме того в случае, когда функции был явно неудачным (макрос FAILED возвращает значение TRUE), расширенные сведения об ошибке можно получить на драйвер OLE DB для SQL Server ошибки интерфейсов.  
  
 Драйвер OLE DB для SQL Server потребителей часто сталкиваются возврата HRESULT DB_S_ERRORSOCCURRED «успеха с оговорками». Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Нет сведений об ошибке могут быть доступны потребителю, возвращаемые в параметрах значение состояния, потребители должны реализовать логику приложения для получения значения состояния, если они доступны.  
  
 Драйвер OLE DB для SQL Server функций-членов не возвращают код успеха S_FALSE. Все драйвер OLE DB для SQL Server функции-члены всегда возвращает значение S_OK, в случае успеха.  
  
## <a name="see-also"></a>См. также  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  

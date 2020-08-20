---
description: Освобождение дескриптора инструкции
title: Освобождение маркера инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5cf58becc532153617ebcbd3cafc6c89d21b4d00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499207"
---
# <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Многократное использование дескрипторов инструкций значительно эффективнее, чем их удаление и повторное выделение. Перед выполнением новой инструкции SQL через дескриптор приложение должно проверить правильность текущих параметров инструкции, в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и результирующие наборы для старой инструкции SQL должны быть отменены путем вызова [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметрами SQL_RESET_PARAMS и SQL_UNBIND и повторной привязки для новой инструкции SQL.  
  
 Когда приложение завершит работу с инструкцией, оно вызывает [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) , чтобы освободить инструкцию. Обратите внимание, что **SQLDisconnect** автоматически освобождает все инструкции по соединению.  
  
## <a name="see-also"></a>См. также:  
 [Выполняя запросы &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  

---
title: Освобождение дескриптора инструкции | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 28a81c55fadcff18862764a6adee548711fd0a8c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32944249"
---
# <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Многократное использование дескрипторов инструкций значительно эффективнее, чем их удаление и повторное выделение. Перед выполнением новой инструкции SQL через дескриптор приложение должно проверить правильность текущих параметров инструкции, в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметров и результирующих наборов для старой инструкции SQL должно ограничиваться путем вызова [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметрами SQL_RESET_PARAMS и SQL_UNBIND параметры и затем повторно привязаны для новой инструкции SQL.  
  
 Когда приложение завершило инструкцией, он вызывает [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) освободить инструкцию. Обратите внимание, что **SQLDisconnect** автоматически освобождает все инструкции для подключения.  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  

---
title: Освобождение ручки заявления (ru) Документы Майкрософт
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
ms.openlocfilehash: 7e954773f85afc434d1e5bd18f7ffb76e28a1438
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297901"
---
# <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Многократное использование дескрипторов инструкций значительно эффективнее, чем их удаление и повторное выделение. Перед выполнением новой инструкции SQL через дескриптор приложение должно проверить правильность текущих параметров инструкции, в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и наборы результатов для старого оператора S'L должны быть не связаны, позвонив в [S'LFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с SQL_RESET_PARAMS и SQL_UNBIND опций, а затем повторно привязаны к новому заявлению S'L.  
  
 Когда приложение закончило использовать выписку, оно вызывает [S'LFreeHandle,](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) чтобы освободить выписку. Обратите внимание, что **S'LDisconnect** автоматически освобождает все операторы на подключение.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов &#40;&#41;ODBC](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  

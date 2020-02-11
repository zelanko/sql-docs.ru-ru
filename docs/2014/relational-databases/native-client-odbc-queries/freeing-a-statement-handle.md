---
title: Освобождение маркера инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b1a155f7d2ee6cc5f92d46c2bb744168dc5ebc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63200045"
---
# <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции
  Многократное использование дескрипторов инструкций значительно эффективнее, чем их удаление и повторное выделение. Перед выполнением новой инструкции SQL через дескриптор приложение должно проверить правильность текущих параметров инструкции, в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и результирующие наборы для старой инструкции SQL должны быть отменены путем вызова [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) с параметрами SQL_RESET_PARAMS и SQL_UNBIND и повторной привязки для новой инструкции SQL.  
  
 Когда приложение завершит работу с инструкцией, оно вызывает [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) , чтобы освободить инструкцию. Обратите внимание, что **SQLDisconnect** автоматически освобождает все инструкции по соединению.  
  
## <a name="see-also"></a>См. также:  
 [Выполняя запросы &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  

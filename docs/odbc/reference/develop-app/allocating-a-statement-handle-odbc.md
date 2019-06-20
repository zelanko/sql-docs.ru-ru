---
title: Выделение дескриптора инструкции ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9524f2e6b01d2a5827dcface3159b7c52a728c59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287873"
---
# <a name="allocating-a-statement-handle-odbc"></a>Выделение дескриптора инструкции (ODBC)
Прежде чем приложение может выполнить инструкцию, оно должно выделить дескриптор инструкции следующим образом:  
  
1.  Приложение объявляет переменную типа HSTMT. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной, дескриптор подключения, в котором для выделения инструкцию, а параметр значение SQL_HANDLE_STMT. Пример:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру, в котором хранятся сведения об инструкции и вызовы **SQLAllocHandle** в драйвере с параметром значение SQL_HANDLE_STMT.  
  
3.  Драйвер выделяет отдельную структуру, в котором хранятся сведения об инструкции и возвращает дескриптор инструкция драйвера диспетчера драйверов.  
  
4.  Диспетчер драйверов возвращает дескриптор инструкции диспетчера драйверов в приложение в переменную приложения.  
  
 Дескриптор инструкции определяет какие инструкция, которая будет использоваться при вызове функций ODBC. Дополнительные сведения о дескрипторов инструкций, см. в разделе [дескрипторов инструкций](../../../odbc/reference/develop-app/statement-handles.md).

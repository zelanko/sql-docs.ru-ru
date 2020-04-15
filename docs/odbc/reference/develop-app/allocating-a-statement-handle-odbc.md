---
title: Распределение выписки Ручка ODBC (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9a15bc4622b15afa9838327edd90383a812270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288434"
---
# <a name="allocating-a-statement-handle-odbc"></a>Выделение дескриптора инструкции (ODBC)
Прежде чем приложение может выполнить заявление, оно должно выделить ручку оператора следующим образом:  
  
1.  Приложение объявляет переменную типа HSTMT. Затем он вызывает **s'LAllocHandle** и передает адрес этой переменной, ручку соединения, в которой выделено заявление, и SQL_HANDLE_STMT опцию. Пример:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Менеджер драйвера выделяет структуру, в которой для хранения информации о выписке и вызывает **s'LAllocHandle** в драйвере с SQL_HANDLE_STMT опцией.  
  
3.  Водитель выделяет собственную структуру, в которой для хранения информации о выписке и возвращает ручку оператора драйвера менеджеру драйвера.  
  
4.  Менеджер драйвера возвращает обработку оператора драйвера в приложение в переменной приложения.  
  
 Ручка оператора определяет, какое заявление использовать при вызове функций ODBC. Для получения дополнительной информации [Statement Handles](../../../odbc/reference/develop-app/statement-handles.md)о ручках оператора см.

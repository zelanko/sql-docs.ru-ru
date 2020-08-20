---
description: Выделение дескриптора инструкции (ODBC)
title: Выделение обработчика операторов ODBC | Документация Майкрософт
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
ms.openlocfilehash: 624490beee55c7fa37346087fc85b560904f6b93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487547"
---
# <a name="allocating-a-statement-handle-odbc"></a>Выделение дескриптора инструкции (ODBC)
Прежде чем приложение сможет выполнить инструкцию, оно должно выделить маркер инструкции следующим образом:  
  
1.  Приложение объявляет переменную типа ХСТМТ. Затем он вызывает **функцию SQLAllocHandle** и передает адрес этой переменной, маркер соединения, в котором выделяется инструкция, и параметр SQL_HANDLE_STMT. Например:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру, в которой хранятся сведения о инструкции, и вызывает **функцию SQLAllocHandle** в драйвере с параметром SQL_HANDLE_STMT.  
  
3.  Драйвер выделяет собственную структуру, в которой хранятся сведения об инструкции, и возвращает диспетчеру драйверов маркер инструкции драйвера.  
  
4.  Диспетчер драйверов Возвращает обработчик драйвера диспетчера драйверов приложению в переменной приложения.  
  
 Маркер инструкции определяет, какую инструкцию следует использовать при вызове функций ODBC. Дополнительные сведения о дескрипторах инструкций см. в разделе [дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md).

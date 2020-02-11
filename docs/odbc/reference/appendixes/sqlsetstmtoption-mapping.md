---
title: Сопоставление SQLSetStmtOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc4ed430b301f2b191c0586c0a54af19a2d2d526
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091672"
---
# <a name="sqlsetstmtoption-mapping"></a>Сопоставление SQLSetStmtOption
Когда приложение вызывает **SQLSetStmtOption** через драйвер ODBC *3. x* , вызов метода  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 результат будет следующим:  
  
-   Если *параметром fOption* указывает на определенный ODBC атрибут инструкции, являющийся строкой, диспетчер драйверов вызывает метод  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *параметром fOption* указывает атрибут инструкции, определяемый ODBC, возвращающий 32-разрядное целое число, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Если *параметром fOption* указывает на определенный драйвером атрибут инструкции, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 В предыдущих трех случаях аргументу **статеменсандле** присваивается значение в *хстмт*, аргументу *атрибута* присваивается значение в *параметром fOption*, а аргументу *ValuePtr* присваивается значение, равное *впарам*.  
  
 Поскольку диспетчер драйверов не знает, требуется ли атрибуту инструкции, определяемому драйвером, строковое или 32-разрядное целое число, оно должно передавать допустимое значение ** аргумента StringLength **SQLSetStmtAttr**. Если драйвер определил специальную семантику для атрибутов инструкций, определяемых драйвером, и должен вызываться с помощью **SQLSetStmtOption**, он должен поддерживать **SQLSetStmtOption**.  
  
 Если приложение вызывает **SQLSetStmtOption** для задания параметра инструкции для конкретного драйвера в драйвере ODBC *3. x* и параметр был определен в версии драйвера ODBC *2. x* , для параметра в драйвере ODBC *3. x* должна быть определена новая константа манифеста. Если в вызове **SQLSetStmtOption**используется старая константа манифеста, диспетчер драйверов выдаст **SQLSetStmtAttr** с аргументом *StringLength* , для которого установлено значение 0.  
  
 Когда приложение вызывает **SQLSetStmtAttr** , чтобы задать для SQL_ATTR_USE_BOOKMARKS SQL_UB_ON в драйвере ODBC *3. x* , атрибуту инструкции SQL_ATTR_USE_BOOKMARKS присваивается значение SQL_UB_FIXED. SQL_UB_ON — это та же самая константа, что и SQL_UB_FIXED. Диспетчер драйверов передает SQL_UB_FIXED в драйвер. SQL_UB_FIXED не рекомендуется использовать в ODBC *3. x*, но драйвер ODBC *3. x* должен реализовать его для работы с приложениями ODBC *2. x* , использующими закладки фиксированной длины.  
  
 Для драйвера ODBC *3. x* диспетчер драйверов больше не проверяет, находится ли *параметр* между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX или больше SQL_CONNECT_OPT_DRVR_START.

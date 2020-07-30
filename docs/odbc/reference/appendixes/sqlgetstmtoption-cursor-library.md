---
title: SQLGetStmtOption (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Cursor Library
ms.assetid: 986170b3-fba8-4323-9224-60b381c7effb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa33df432463779f397fee2dcd50b06443082c52
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362941"
---
# <a name="sqlgetstmtoption-cursor-library"></a>SQLGetStmtOption (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLGetStmtOption** в библиотеке курсоров. Общие сведения о **SQLGetStmtOption**см. в разделе [функция SQLGetStmtOption](../../../odbc/reference/syntax/sqlgetstmtoption-function.md).  
  
 Библиотека курсоров поддерживает следующие параметры инструкции с **SQLGetStmtOption**:  

:::row:::
    :::column:::
        SQL_BIND_TYPE  
        SQL_CONCURRENCY  
        SQL_CURSOR_TYPE  
        SQL_GET_BOOKMARK  
    :::column-end:::
    :::column:::
        SQL_ROW_NUMBER  
        SQL_ROWSET_SIZE  
        SQL_SIMULATE_CURSOR  
    :::column-end:::
:::row-end:::

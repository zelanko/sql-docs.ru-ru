---
title: SQLSetPos (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b41fad0f609b16640bfa28ab36f29f364e067b73
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63297419"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLSetPos** функции в библиотеку курсоров. Общие сведения о **SQLSetPos**, см. в разделе [функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
 Библиотека курсоров поддерживает операцию SQL_POSITION только для *операции* аргумента в **SQLSetPos**. Он поддерживает SQL_LOCK_NO_CHANGE значение только для *LockType* аргумент.  
  
 Если драйвер не поддерживает массовых операций, библиотека курсоров возвращает SQLSTATE HYC00 (драйвер для не поддерживающих) при **SQLSetPos** вызывается с *RowNumber* равно 0. Это поведение драйвера не рекомендуется.  
  
 Библиотека курсоров не поддерживает операции SQL_UPDATE и SQL_DELETE в вызове **SQLSetPos**. Библиотека реализует курсор, позиционированные обновления или удаления инструкции SQL, создав искомая инструкция update или delete с предложением WHERE, который перечисляет значения, хранящиеся в кэше для каждого привязанного столбца. Дополнительные сведения см. в разделе [обработки расположен обновления и удаления инструкций](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md).  
  
 Если драйвер не поддерживает статические курсоры, приложение, которое работает с библиотекой курсоров должны вызывать **SQLSetPos** только для набора строк, выбрать с помощью **SQLExtendedFetch** или **SQLFetchScroll** , а не по **SQLFetch**. Библиотека курсоров реализует **SQLExtendedFetch** и **SQLFetchScroll** обращаясь из **SQLFetch** (с размером набора строк, 1) в драйвере. Библиотека курсоров передает вызовы **SQLFetch**, но другой стороны, новые через к драйверу. Если **SQLSetPos** вызывается для набора строк несколькими строками, выбрать с помощью **SQLFetch** Если драйвер не поддерживает статические курсоры, вызов завершится ошибкой, так как **SQLSetPos** не работает с помощью курсоров. Это происходит, даже если приложение успешно вызвал **SQLSetStmtAttr** присвоить SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, которая поддерживает библиотеку курсоров, даже если драйвер не поддерживает статические курсоры.

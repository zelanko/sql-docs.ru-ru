---
title: SQLSetConnectAttr (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d10356488b0a590fb065c49a36a05f0e9b976991
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetConnectAttr** функции в библиотеку курсоров. Общие сведения о **SQLSetConnectAttr**, в разделе [SQLSetConnectAttr, функция](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Приложение вызывает **SQLSetConnectAttr** , атрибут SQL_ATTR_ODBC_CURSORS для указания ли библиотека курсоров всегда используется, если драйвер не поддерживает прокручиваемые курсоры или никогда не используется. Библиотека курсоров предполагается, драйвер поддерживает прокручиваемые курсоры, если он возвращает SQL_CA1_RELATIVE для типа данных SQL_STATIC_CURSOR_ATTRIBUTES1 в **SQLGetInfo**.  
  
 Приложение должно вызвать **SQLSetConnectAttr** для указания библиотеки использование курсора после вызова **SQLAllocHandle** с *HandleType* установленным в значение sql_handle_dbc для выделения подключение и до подключения к источнику данных. Если приложение вызывает **SQLSetConnectAttr** , атрибут SQL_ATTR_ODBC_CURSORS во время подключения по-прежнему активна, библиотеку курсоров возвращает сообщение об ошибке.  
  
 Чтобы задать атрибут инструкции, поддерживаемые библиотекой курсоров для всех инструкций, ассоциированные с соединением, приложение должно вызвать **SQLSetConnectAttr** для этого атрибута инструкции после подключения к источнику данных и перед его Открывает курсор. Если приложение вызывает **SQLSetConnectAttr** с помощью оператора атрибута и курсор открыт на инструкции, связанные с подключением, атрибут инструкции не будут применяться к этой инструкции, пока курсор не будет закрыт и повторно.

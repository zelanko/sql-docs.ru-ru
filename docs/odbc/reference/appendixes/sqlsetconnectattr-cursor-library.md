---
title: SQLSetConnectAttr (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d4023c513ffda04a3cf499110185d3746ca40d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713462"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLSetConnectAttr** функции в библиотеку курсоров. Общие сведения о **SQLSetConnectAttr**, см. в разделе [SQLSetConnectAttr, функция](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Приложение вызывает **SQLSetConnectAttr** атрибутом SQL_ATTR_ODBC_CURSORS, чтобы указать ли библиотека курсоров всегда используется, если драйвер не поддерживает прокручиваемые курсоры или никогда не используется. Библиотека курсоров предполагается, что драйвер поддерживает прокручиваемые курсоры, если он возвращает SQL_CA1_RELATIVE для типа данных SQL_STATIC_CURSOR_ATTRIBUTES1 в **SQLGetInfo**.  
  
 Приложение должно вызвать **SQLSetConnectAttr** указание использование библиотеки курсоров после вызова **SQLAllocHandle** с *HandleType* из SQL_HANDLE_DBC для выделения подключение и до подключения к источнику данных. Если приложение вызывает **SQLSetConnectAttr** с атрибутом SQL_ATTR_ODBC_CURSORS во время подключения по-прежнему активна, библиотека курсоров возвращает сообщение об ошибке.  
  
 Чтобы задать атрибут инструкции, поддерживаемые библиотекой курсоров для всех инструкций, ассоциированные с соединением, приложение должно вызвать **SQLSetConnectAttr** для этого атрибута инструкции после подключения к источнику данных и до ее Открывает курсор. Если приложение вызывает **SQLSetConnectAttr** с помощью оператора атрибута, так и курсор открыт в операторе, связанный с подключением, атрибут инструкции не будет применяться с инструкцией, пока не будет закрыт курсор и повторно.

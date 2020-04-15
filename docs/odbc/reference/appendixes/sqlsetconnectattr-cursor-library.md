---
title: СЗЛСетКоннЕКТтр (Библиотека Курсора) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a87c85d727fb9eb2fc27613b9eecd3fe0ec51b58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300544"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LSetConnectAttr** в библиотеке курсоров. Для получения общей информации о **функции S'LsetConnectattr**см. [SQLSetConnectAttr Function](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
 Приложение вызывает **S'LSetConnectAttr** с SQL_ATTR_ODBC_CURSORS атрибутом, чтобы указать, всегда ли используется библиотека курсора, если драйвер не поддерживает прокрутки курсоров или никогда не используется. Библиотека курсора предполагает, что драйвер поддерживает прокрутки курсоры, если он возвращает SQL_CA1_RELATIVE для SQL_STATIC_CURSOR_ATTRIBUTES1 типа информации в **S'LGetInfo.**  
  
 Приложение должно позвонить в **S'LSetConnectAttr,** чтобы указать использование библиотеки курсоров после того, как оно вызывает **S'LAllocHandle** с *помощью handleType* SQL_HANDLE_DBC для выделения соединения и до того, как оно подключится к источнику данных. Если приложение вызывает **S'LSetConnectAttr** с SQL_ATTR_ODBC_CURSORS атрибутом, пока соединение еще активен, библиотека курсора возвращает ошибку.  
  
 Чтобы настроить атрибут оператора, поддерживаемый библиотекой курсора для всех инструкций, связанных с соединением, приложение должно вызвать атрибут **s'LSetConnectAttr** для этого атрибута оператора после подключения к источнику данных и перед тем, как он откроет курсор. Если приложение вызывает **s'LSetConnectAttr** с атрибутом оператора, а курсор открыт для оператора, связанного с соединением, атрибут оператора не будет применяться к этому заявлению до тех пор, пока курсор не будет закрыт и не открыт.

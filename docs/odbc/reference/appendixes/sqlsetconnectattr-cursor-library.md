---
description: SQLSetConnectAttr (библиотека курсоров)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b809ad81e9edaca7fbe7d40952673a1698f113e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424896"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLSetConnectAttr** в библиотеке курсоров. Общие сведения о **SQLSetConnectAttr**см. в разделе [функция SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Приложение вызывает **SQLSetConnectAttr** с атрибутом SQL_ATTR_ODBC_CURSORS, чтобы указать, всегда ли используется библиотека курсоров, используется, если драйвер не поддерживает прокручиваемые курсоры или никогда не используется. Библиотека курсоров предполагает, что драйвер поддерживает прокручиваемые курсоры, если он возвращает SQL_CA1_RELATIVE для типа сведений о SQL_STATIC_CURSOR_ATTRIBUTES1 в **SQLGetInfo**.  
  
 Приложение должно вызвать **SQLSetConnectAttr** , чтобы указать использование библиотеки курсоров после вызова **функцию sqlallochandle** с *параметром handletype* SQL_HANDLE_DBC для выделения соединения и перед подключением к источнику данных. Если приложение вызывает **SQLSetConnectAttr** с атрибутом SQL_ATTR_ODBC_CURSORS, пока соединение все еще активно, Библиотека курсоров возвращает ошибку.  
  
 Чтобы задать атрибут инструкции, поддерживаемый библиотекой курсоров, для всех инструкций, связанных с соединением, приложение должно вызвать **SQLSetConnectAttr** для этого атрибута инструкции после подключения к источнику данных и перед открытием курсора. Если приложение вызывает **SQLSetConnectAttr** с атрибутом инструкции и курсор открыт в инструкции, связанной с соединением, атрибут инструкции не будет применен к этой инструкции до тех пор, пока курсор не будет закрыт и открыт повторно.

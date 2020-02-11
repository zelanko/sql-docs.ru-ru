---
title: SQLGetFunctions (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1497a7d2ec5951feedb36831ab541413e57152f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073923"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLGetFunctions** в библиотеке курсоров. Общие сведения о **SQLGetFunctions**см. в разделе [функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 При вызове **SQLGetFunctions**библиотека курсоров возвращает, что она поддерживает **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**и **SQLSetScrollOptions**в дополнение к функциям, поддерживаемым драйвером.

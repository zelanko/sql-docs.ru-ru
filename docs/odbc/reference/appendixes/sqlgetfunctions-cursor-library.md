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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073923"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLGetFunctions** функции в библиотеку курсоров. Общие сведения о **SQLGetFunctions**, см. в разделе [функция SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 При вызове **SQLGetFunctions**, библиотека курсоров возвращает, что он поддерживает **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, и **SQLSetScrollOptions**, в дополнение к функциям, поддерживаемых драйвером.

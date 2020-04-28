---
title: SQLFreeStmt (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78075593926c15dbaeb1904603b08e990f64983
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302025"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLFreeStmt** в библиотеке курсоров. Общие сведения о **SQLFreeStmt**см. в разделе [Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Если приложение вызывает **SQLFreeStmt** с параметром SQL_UNBIND после вызова **SQLExtendedFetch**, **SQLFetch**или **SQLFetchScroll**, Библиотека курсоров возвращает ошибку. Прежде чем можно будет отменить привязку столбцов результирующего набора, приложение должно вызвать **SQLCloseCursor** или **SQLFreeStmt** с параметром SQL_CLOSE.

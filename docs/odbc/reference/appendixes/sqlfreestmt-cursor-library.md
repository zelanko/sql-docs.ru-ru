---
description: SQLFreeStmt (библиотека курсоров)
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
ms.openlocfilehash: 9bc9ba1bc747f2c4408c308b13924afc8b3ba875
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448994"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLFreeStmt** в библиотеке курсоров. Общие сведения о **SQLFreeStmt**см. в разделе [Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Если приложение вызывает **SQLFreeStmt** с параметром SQL_UNBIND после вызова **SQLExtendedFetch**, **SQLFetch**или **SQLFetchScroll**, Библиотека курсоров возвращает ошибку. Прежде чем можно будет отменить привязку столбцов результирующего набора, приложение должно вызвать **SQLCloseCursor** или **SQLFreeStmt** с параметром SQL_CLOSE.

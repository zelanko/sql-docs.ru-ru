---
title: СЗЛФриСтмт (Библиотека Курзора) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302025"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LFreeStmt** в библиотеке курсоров. Для получения общей информации о **функциях S'LFreeStmt см.** [SQLFreeStmt Function](../../../odbc/reference/syntax/sqlfreestmt-function.md)  
  
 Если приложение вызывает **s'LFreeStmt** с опцией SQL_UNBIND после того, как оно вызывает **S'LExtendedFetch**, **S'LFetch**, или **S'LFetchScroll**, библиотека курсора возвращает ошибку. Прежде чем он сможет отменить столбцы набора результатов, приложение должно вызвать **S'LCloseCursor** или **S'LFreeStmt** с SQL_CLOSE опцией.

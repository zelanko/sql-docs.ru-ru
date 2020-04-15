---
title: СЗЛРасширенныйЧт (Библиотека Курзора) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe39b2d2cbbaf72ce3844c35187040589d1dac58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302065"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LExtendedFetch** в библиотеке курсоров. Для получения общей информации о **S'LExtendedFetch**, [см.](../../../odbc/reference/syntax/sqlextendedfetch-function.md)  
  
 Библиотека курсоров, выполняющая программу **S'LExtendedFetch,** по-неоднократно вызывала **s'LFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов **S'LExtendedFetch** с *Помощью SQL_FETCH_BOOKMARK.*  
  
 При использовании библиотеки курсоров, вызовы на **S'LExtendedFetch** не могут быть смешаны с вызовами либо в **S'LFetchScroll,** либо **на S'LFetchFetchScroll или S'LFetch.**

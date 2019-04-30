---
title: SQLFetch (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 487a6b357d21ee675fa9594d32c7a2bb7c66e400
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199488"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLFetch** функции в библиотеку курсоров. Общие сведения о **SQLFetch**, см. в разделе [SQLFetch, функция](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 При использовании библиотеки курсоров вызовы **SQLFetch** нельзя комбинировать с вызовами либо **SQLFetchScroll** или **SQLExtendedFetch**.  
  
 Если **SQLFetch** вызывается с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE присвоено значение больше 1, библиотека курсоров передает вызов к драйверу. Если драйвер ODBC 2. *x* драйвера, будет игнорироваться размер набора строк и вызовом **SQLFetch** возвращает одну строку данных.  
  
 Если используется библиотека курсоров ODBC 2. *x* драйвер, связывающего смещение (в соответствии с атрибут инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR) не используется, когда **SQLFetch** вызывается.  
  
 При загрузке библиотеки курсоров, приложение не может вызвать **SQLFetch** получить столбцы закладок. Библиотека курсоров передает вызов **SQLFetch** через драйвер, но функция вызовы включить закладки и привязать столбец закладки могут быть перехвачены библиотекой курсоров.

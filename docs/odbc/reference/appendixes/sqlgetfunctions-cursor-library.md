---
title: "SQLGetFunctions (библиотека курсоров) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d8ca656e63183df424de2ec45c823ac275ef69f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLGetFunctions** функции в библиотеку курсоров. Общие сведения о **SQLGetFunctions**, в разделе [SQLGetFunctions, функция](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 При вызове **SQLGetFunctions**, возвращает библиотеку курсоров, он поддерживает **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, и **SQLSetScrollOptions**, в дополнение к функциям, поддерживаемых драйвером.


---
title: SQLExtendedFetch (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 573cf41aae6e36db05789908d92fa7ef710a341b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLExtendedFetch** функции в библиотеку курсоров. Общие сведения о **SQLExtendedFetch**, в разделе [SQLExtendedFetch функция](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Библиотека курсоров реализует **SQLExtendedFetch** многократно вызывая **SQLFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов метода **SQLExtendedFetch** с *FetchOrientation* из SQL_FETCH_BOOKMARK.  
  
 При использовании библиотеки курсоров вызовы **SQLExtendedFetch** невозможно комбинировать с вызовами либо **SQLFetchScroll** или **SQLFetch**.

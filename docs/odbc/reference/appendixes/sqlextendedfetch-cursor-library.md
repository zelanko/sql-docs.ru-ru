---
title: "SQLExtendedFetch (библиотека курсоров) | Документы Microsoft"
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
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c39b299dc2f42fdf1eb51010e7b4fac2bb9bcfd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLExtendedFetch** функции в библиотеку курсоров. Общие сведения о **SQLExtendedFetch**, в разделе [SQLExtendedFetch функция](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 Библиотека курсоров реализует **SQLExtendedFetch** многократно вызывая **SQLFetch** в драйвере.  
  
 Библиотека курсоров поддерживает вызов метода **SQLExtendedFetch** с *FetchOrientation* из SQL_FETCH_BOOKMARK.  
  
 При использовании библиотеки курсоров вызовы **SQLExtendedFetch** невозможно комбинировать с вызовами либо **SQLFetchScroll** или **SQLFetch**.


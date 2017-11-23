---
title: "SQLSetEnvAttr и библиотеку курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 481bd456a1dcc75af24777c7db288bd757cc70b9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr и библиотека курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetEnvAttr** функции библиотеки курсоров. Общие сведения о **SQLSetEnvAttr**, в разделе [SQLSetEnvAttr, функция](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Библиотека курсоров не зависит от настройки атрибута среды SQL_ATTR_ODBC_VERSION, независимо от версии приложения или драйвера.

---
title: "SQLSetEnvAttr и библиотеку курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c08fab3b713e1f1a57d7a81f53ed29b1678893cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr и библиотека курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetEnvAttr** функции библиотеки курсоров. Общие сведения о **SQLSetEnvAttr**, в разделе [SQLSetEnvAttr, функция](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Библиотека курсоров не зависит от настройки атрибута среды SQL_ATTR_ODBC_VERSION, независимо от версии приложения или драйвера.

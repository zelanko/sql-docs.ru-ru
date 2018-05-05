---
title: SQLSetEnvAttr и библиотеку курсоров | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba46e2b455c6f2e70d392387a4015cadc1b30a85
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr и библиотека курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetEnvAttr** функции библиотеки курсоров. Общие сведения о **SQLSetEnvAttr**, в разделе [SQLSetEnvAttr, функция](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 Библиотека курсоров не зависит от настройки атрибута среды SQL_ATTR_ODBC_VERSION, независимо от версии приложения или драйвера.

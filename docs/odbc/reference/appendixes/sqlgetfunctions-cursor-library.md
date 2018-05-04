---
title: SQLGetFunctions (библиотека курсоров) | Документы Microsoft
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
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45778aeb876b50e44323f91a0aaf00d480130456
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLGetFunctions** функции в библиотеку курсоров. Общие сведения о **SQLGetFunctions**, в разделе [SQLGetFunctions, функция](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 При вызове **SQLGetFunctions**, возвращает библиотеку курсоров, он поддерживает **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, и **SQLSetScrollOptions**, в дополнение к функциям, поддерживаемых драйвером.

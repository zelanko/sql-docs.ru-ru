---
title: SQLAllocConnect (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2889ef8e5c6f3a0db4e133ddf0bdd51fda338b40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063293"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Уровня ядра  
  
 Выделяет память для дескриптора соединения, *hdbc*, в среду, определяемую по *henv*. Диспетчер драйверов обрабатывает этот вызов и вызывает драйвер **SQLAllocConnect** всякий раз, когда [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**, или [SQLDriverConnect ](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) вызывается.  
  
 Дополнительные сведения см. в разделе [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) в *Справочник по программированию ODBC*.

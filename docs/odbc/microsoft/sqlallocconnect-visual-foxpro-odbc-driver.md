---
description: SQLAllocConnect (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 548d8f1b0c4679f8cbfe8e5af39cfcf592087bc8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483407"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень ядра  
  
 Выделяет память для маркера подключения *хдбк*в среде, определяемой *хенв*. Диспетчер драйверов обрабатывает этот вызов и вызывает **SQLAllocConnect** драйвера каждый раз, когда вызывается [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**или [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) .  
  
 Дополнительные сведения см. в разделе [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) в *справочнике программиста по ODBC*.

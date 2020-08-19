---
description: Escape-последовательность
title: Escape-последовательности | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15c06fc08d78422502b8aea87c40ee2821a9620f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429306"
---
# <a name="escape-sequences"></a>Escape-последовательность
ODBC определяет escape-последовательности, которые содержат стандартную грамматику для литералов даты, времени, timestamp и интервала времени, скалярные вызовы функций, **такие как** escape-символы предиката, внешние соединения и вызовы процедур. Приложения, поддерживающие взаимодействие, должны использовать эти последовательности везде, где это возможно.  
  
 Чтобы определить, поддерживает ли драйвер escape-последовательности для литералов даты, времени, отметке времени или интервала времени, приложение вызывает **SQLGetTypeInfo**. Если источник данных поддерживает тип данных даты, времени, timestamp или DateTime, он также должен поддерживать соответствующую escape-последовательность. Чтобы определить, поддерживаются ли другие escape-последовательности, приложение вызывает **SQLGetInfo**.  
  
 Дополнительные сведения см. в подразделе [escape-последовательности в ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)ниже.

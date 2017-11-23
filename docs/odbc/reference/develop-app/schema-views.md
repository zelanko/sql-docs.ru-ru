---
title: "Представления схемы | Документы Microsoft"
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
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d85a59f54fab5508c5781bfb29a1243c12b44e6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="schema-views"></a>Представления схемы
Приложение может получать сведения метаданных из СУБД, либо путем вызова функций каталога ODBC, либо с помощью представления INFORMATION_SCHEMA. Представления определяются по стандарту ANSI SQL-92.  
  
 Если поддерживается СУБД и драйвер, представления INFORMATION_SCHEMA позволяют более мощных и исчерпывающую получения метаданных более функций каталога ODBC. Приложение может выполнить свою **ВЫБЕРИТЕ** инструкции к одному из этих представлений можно объединять представления или можно выполнять объединение представлений. Предлагая больше программы и более широкий набор метаданных, представления INFORMATION_SCHEMA не часто поддерживаются СУБД. Это может изменить как драйверы и СУБД достижения совместимости с SQL-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **SQLGetInfo** с параметром SQL_INFO_SCHEMA_VIEWS. Для получения метаданных из поддерживаемых представления, приложение выполняет **ВЫБЕРИТЕ** инструкцию, которая указывает необходимые сведения о схеме.

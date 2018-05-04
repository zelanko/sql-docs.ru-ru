---
title: Представления схемы | Документы Microsoft
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
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed8fdc07b884605f1fd2b3c185cf5bef2eedc66b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="schema-views"></a>Представления схемы
Приложение может получать сведения метаданных из СУБД, либо путем вызова функций каталога ODBC, либо с помощью представления INFORMATION_SCHEMA. Представления определяются по стандарту ANSI SQL-92.  
  
 Если поддерживается СУБД и драйвер, представления INFORMATION_SCHEMA позволяют более мощных и исчерпывающую получения метаданных более функций каталога ODBC. Приложение может выполнить свою **ВЫБЕРИТЕ** инструкции к одному из этих представлений можно объединять представления или можно выполнять объединение представлений. Предлагая больше программы и более широкий набор метаданных, представления INFORMATION_SCHEMA не часто поддерживаются СУБД. Это может изменить как драйверы и СУБД достижения совместимости с SQL-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **SQLGetInfo** с параметром SQL_INFO_SCHEMA_VIEWS. Для получения метаданных из поддерживаемых представления, приложение выполняет **ВЫБЕРИТЕ** инструкцию, которая указывает необходимые сведения о схеме.

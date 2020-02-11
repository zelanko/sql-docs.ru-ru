---
title: Представления схемы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e2dd512ab529f1fb5d216f4a2e459cd601d40e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67943758"
---
# <a name="schema-views"></a>Представления схемы
Приложение может извлекать метаданные из СУБД либо путем вызова функций каталога ODBC, либо с помощью INFORMATION_SCHEMA представлений. Представления определяются стандартом ANSI SQL-92.  
  
 Если поддерживается СУБД и драйвером, то INFORMATION_SCHEMA представления предоставляют более мощные и комплексные средства получения метаданных, чем предоставляемые функциями каталога ODBC. Приложение может выполнять собственную пользовательскую инструкцию **SELECT** для одного из этих представлений, может присоединять представления или выполнять объединение представлений. При предложении большей служебной программы и более широкого спектра метаданных, INFORMATION_SCHEMA представления часто не поддерживаются СУБД. Это может измениться по мере того, как больше СУБД и драйверов достигает соответствия с SQL-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **SQLGetInfo** с параметром SQL_INFO_SCHEMA_VIEWS. Чтобы получить метаданные из поддерживаемого представления, приложение выполняет инструкцию **SELECT** , указывающую необходимые сведения о схеме.

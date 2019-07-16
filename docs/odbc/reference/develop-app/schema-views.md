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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67943758"
---
# <a name="schema-views"></a>Представления схемы
Приложение может получать сведения о метаданных от СУБД, либо путем вызова функций каталога ODBC, либо с помощью представления INFORMATION_SCHEMA. Представления определяются по стандарту ANSI SQL-92.  
  
 Если поддерживается СУБД и драйвер, представления INFORMATION_SCHEMA позволяют более эффективных и полнофункциональных получения метаданных, чем предоставить функций каталога ODBC. Приложение может выполнить свою **ВЫБЕРИТЕ** инструкции для одного из этих представлений можно объединить представления, или можно выполнить объединение с представлениями. Предлагая более служебной программы и более широкий набор метаданных, представления INFORMATION_SCHEMA не часто поддерживаются СУБД. Это может быть изменено, так как дополнительные СУБД и драйверов достижение соответствия SQL-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **SQLGetInfo** с параметром SQL_INFO_SCHEMA_VIEWS. Чтобы получить метаданные из поддерживаемых представления, приложение выполняет **ВЫБЕРИТЕ** инструкцию, которая определяет необходимые сведения о схеме.

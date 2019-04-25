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
manager: craigg
ms.openlocfilehash: 782dec08b76a9e5a97719d6af39e2c30c0f92d19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468621"
---
# <a name="schema-views"></a>Представления схемы
Приложение может получать сведения о метаданных от СУБД, либо путем вызова функций каталога ODBC, либо с помощью представления INFORMATION_SCHEMA. Представления определяются по стандарту ANSI SQL-92.  
  
 Если поддерживается СУБД и драйвер, представления INFORMATION_SCHEMA позволяют более эффективных и полнофункциональных получения метаданных, чем предоставить функций каталога ODBC. Приложение может выполнить свою **ВЫБЕРИТЕ** инструкции для одного из этих представлений можно объединить представления, или можно выполнить объединение с представлениями. Предлагая более служебной программы и более широкий набор метаданных, представления INFORMATION_SCHEMA не часто поддерживаются СУБД. Это может быть изменено, так как дополнительные СУБД и драйверов достижение соответствия SQL-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **SQLGetInfo** с параметром SQL_INFO_SCHEMA_VIEWS. Чтобы получить метаданные из поддерживаемых представления, приложение выполняет **ВЫБЕРИТЕ** инструкцию, которая определяет необходимые сведения о схеме.

---
title: Виды схемы Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1a9e421c4835d35e3c4f3c644e69b8c7601e8e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304255"
---
# <a name="schema-views"></a>Представления схемы
Приложение может получать информацию о метаданных из DBMS либо путем вызова функций каталога ODBC, либо с помощью INFORMATION_SCHEMA представлений. Представления определяются стандартом ANSI S'L-92.  
  
 При поддержке DBMS и драйвера INFORMATION_SCHEMA представления обеспечивают более мощное и всеобъемлющее средство получения метаданных, чем предоставляют функции каталога ODBC. Приложение может выполнять свое собственное пользовательское заявление **SELECT** в отношении одного из этих представлений, может присоединиться к представлениям или выполнять союз по представлениям. Предлагая большую полезность и более широкий спектр метаданных, INFORMATION_SCHEMA мнения не часто поддерживаются DBMS. Это может измениться по мере того, как больше DBMS и драйверы достигают соответствия с S'L-92.  
  
 Чтобы определить, какие представления поддерживаются, приложение вызывает **s'LGetInfo** с опцией SQL_INFO_SCHEMA_VIEWS. Для извлечения метаданных из поддерживаемого представления приложение выполняет заявление **SELECT,** в котором указана необходимая информация о схеме.

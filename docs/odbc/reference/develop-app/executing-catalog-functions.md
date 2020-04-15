---
title: Выполнение функций каталога (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6469a5394e232ab9d9135fbbbd56ba7b791ccbcb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305725"
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Поскольку функция каталога создает набор результатов, она эквивалентна выполнением любого оператора, генерирующего результаты, s'L. На самом деле функции каталога часто реализуются путем выполнения предопределенных инструкций s-L или вызова предопределенных процедур, которые поставляются с драйвером или DBMS. Почти все, что применимо к инструкциям S'L, которые создают наборы результатов, также относится к функциям каталога. Например, атрибут SQL_ATTR_MAX_ROWS оператора ограничивает количество строк, возвращенных функцией каталога, точно так же, как и ограничение числа строк, вернувшихся в оператора **SELECT.**  
  
 Чтобы выполнить функцию каталога, приложение просто вызывает функцию.  
  
 Для получения дополнительной информации о функциях каталога [см.](../../../odbc/reference/develop-app/catalog-functions.md)

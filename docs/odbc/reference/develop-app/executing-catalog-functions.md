---
title: Выполняя функции каталога | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305725"
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Поскольку функция каталога создает результирующий набор, она эквивалентна выполнению любой инструкции SQL, создающей результирующий набор. Фактически, функции каталога часто реализуются путем выполнения предопределенных инструкций SQL или вызова стандартных процедур, поставляемых с драйвером или СУБД. Практически все, что применяется к инструкциям SQL, которые создают результирующие наборы, также применяются к функциям каталога. Например, атрибут оператора SQL_ATTR_MAX_ROWS ограничивает количество строк, возвращаемых функцией каталога, точно так же, как это ограничивает число строк, возвращаемых инструкцией **SELECT** .  
  
 Для выполнения функции каталога приложение просто вызывает функцию.  
  
 Дополнительные сведения о функциях каталога см. в разделе [функции каталога](../../../odbc/reference/develop-app/catalog-functions.md).

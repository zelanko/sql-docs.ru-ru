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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ab6eba9c4a3df3e16e35d8a93dc95209a093fb80
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901276"
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Поскольку функция каталога создает результирующий набор, она эквивалентна выполнению любой инструкции SQL, создающей результирующий набор. Фактически, функции каталога часто реализуются путем выполнения предопределенных инструкций SQL или вызова стандартных процедур, поставляемых с драйвером или СУБД. Практически все, что применяется к инструкциям SQL, которые создают результирующие наборы, также применяются к функциям каталога. Например, атрибут оператора SQL_ATTR_MAX_ROWS ограничивает количество строк, возвращаемых функцией каталога, точно так же, как это ограничивает число строк, возвращаемых инструкцией **SELECT** .  
  
 Для выполнения функции каталога приложение просто вызывает функцию.  
  
 Дополнительные сведения о функциях каталога см. в разделе [функции каталога](../../../odbc/reference/develop-app/catalog-functions.md).

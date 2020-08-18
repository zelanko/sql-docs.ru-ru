---
description: Выполнение функций каталога
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
ms.openlocfilehash: 19baae1518078c44b8e170fb623eab0087bac12a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482917"
---
# <a name="executing-catalog-functions"></a>Выполнение функций каталога
Поскольку функция каталога создает результирующий набор, она эквивалентна выполнению любой инструкции SQL, создающей результирующий набор. Фактически, функции каталога часто реализуются путем выполнения предопределенных инструкций SQL или вызова стандартных процедур, поставляемых с драйвером или СУБД. Практически все, что применяется к инструкциям SQL, которые создают результирующие наборы, также применяются к функциям каталога. Например, атрибут оператора SQL_ATTR_MAX_ROWS ограничивает количество строк, возвращаемых функцией каталога, точно так же, как это ограничивает число строк, возвращаемых инструкцией **SELECT** .  
  
 Для выполнения функции каталога приложение просто вызывает функцию.  
  
 Дополнительные сведения о функциях каталога см. в разделе [функции каталога](../../../odbc/reference/develop-app/catalog-functions.md).

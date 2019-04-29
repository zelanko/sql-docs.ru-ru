---
title: Функции работы с каталогами | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 268d5f00d787cef8dfdcb29bd9e091f81a5ed2c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63125589"
---
# <a name="catalog-functions"></a>Функции работы с каталогами
Все базы данных имеют структуру, описывающий, каким образом данные будут храниться в базе данных. Например база данных простой заказа на продажу может иметь структуру, представленную на следующем рисунке, в котором используются столбцы идентификатора установить связь между таблицами.  
  
 ![Показана структура простой базы данных](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Эта структура, вместе с другими сведениями, например права доступа, хранится в набор системных таблиц, именем базы данных *каталога,* который также называется *словарь данных*.  
  
 Приложение может обнаружить эту структуру через вызовы к *функции работы с каталогами*. Функции каталога возвращают сведения в результирующих наборов они обычно реализуется через **ВЫБЕРИТЕ** инструкции к таблицам в каталоге. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Функции работы с каталогами в ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

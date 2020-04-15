---
title: Функции каталога Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb28ec6f4ea299dae8737fc707fd53e4d102442d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305205"
---
# <a name="catalog-functions"></a>Функции работы с каталогами
Все базы данных имеют структуру, в которой излагается, как данные будут храниться в базе данных. Например, простая база данных заказов на продажу может иметь структуру, показанную на следующей иллюстрации, в которой столбцы идентификаторов используются для связи таблиц.  
  
 ![Структура простой базы данных](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Эта структура, наряду с другой информацией, такой как привилегии, хранится в наборе системных таблиц, называемых *каталогом* базы данных, который также известен как *словарь данных.*  
  
 Приложение может обнаружить эту структуру с помощью вызовов в *функции каталога.* Функции каталога возвращают информацию в наборах результатов и обычно реализуются через заявления **SELECT** в таблицах каталога. Например, приложение может запросить результирующий набор, содержащий сведения о всех таблицах в системе или всех столбцах в определенной таблице.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Функции работы с каталогами в ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

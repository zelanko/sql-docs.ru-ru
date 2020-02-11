---
title: Удаление строк из набора строк с помощью функции SQLSetPos | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39b70f92f7b239b011cdd4fdd6abd36c27561c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076802"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Удаление строк в наборе строк с помощью SQLSetPos
Операция удаления функции **SQLSetPos** позволяет источнику данных удалить одну или несколько выбранных строк таблицы. Чтобы удалить строки с помощью функции **SQLSetPos**, приложение вызывает функцию **SQLSetPos** с набором *операций* SQL_DELETE, а функция *RowNumber* задает номер удаляемой строки. Если параметр *RowNumber* имеет значение 0, все строки в наборе строк удаляются.  
  
 После возврата функции **SQLSetPos** удаленная строка будет текущей строкой, а ее состояние будет SQL_ROW_DELETED. Строку нельзя использовать в последующих позиционированных операциях, например в вызовах **SQLGetData** или **SQLSetPos**.  
  
 При удалении всех строк набора строк (*RowNumber* равен 0) приложение может запретить драйверу удалять определенные строки, используя массив операций строк, так же, как и операция обновления **SQLSetPos**. (См. раздел [Обновление строк в наборе строк с помощью функции SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения были заполнены путем выборки и если массив состояния строки был сохранен, то его значения в каждой из этих положений строки не должны быть SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.

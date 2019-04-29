---
title: Удаление строк в наборе строк с помощью SQLSetPos | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 78ee14838b467cfe6e555c97f1e74c65cccf98ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049834"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Удаление строк в наборе строк с помощью SQLSetPos
Операция удаления **SQLSetPos** позволяет удалить один или несколько выбранных строк таблицы источника данных. Для удаления строк с **SQLSetPos**, приложение вызывает **SQLSetPos** с *операции* значение SQL_DELETE и *RowNumber* значение Номер строки для удаления. Если *RowNumber* равно 0, то удаляются все строки в наборе строк.  
  
 После **SQLSetPos** возвращает Удаленная строка является текущей строки, а ее состояние имеет значение SQL_ROW_DELETED. Строка не может использоваться в любой дальнейшей позиционированные операции, такие как вызовы **SQLGetData** или **SQLSetPos**.  
  
 При удалении всех строк набора строк (*RowNumber* равно 0), приложение может предотвратить удаление определенных строк с помощью массива операций строк, так же как и для операций обновления драйвера **SQLSetPos** . (См. в разделе [обновление строк в наборе строк с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения заполняются выборкой, а массив состояния строк была сохранена, значения каждой из этих позиций строк не должно быть значение SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.

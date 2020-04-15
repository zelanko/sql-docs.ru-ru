---
title: Удаляя строки в Роусете с помощью S'LSetPos (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940bcc3e2ee6a042394797d6038028cce64862f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305955"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Удаление строк в наборе строк с помощью SQLSetPos
Операция удаления **S'LSetPos** заставляет источник данных удалять один или несколько выбранных строк таблицы. Для удаления строк с **помощью S'LSetPos**приложение вызывает **S'LSetPos** с *операцией,* установленной для SQL_DELETE и *RowNumber,* установленным на номер строки для удаления. Если *rowNumber* равен 0, все строки в наборе строк удаляются.  
  
 После возвращения **S'LSetPos** удаленная строка — это текущая строка, а ее статус SQL_ROW_DELETED. Строка не может быть использована в любых дальнейших операциях, расположенных, таких как вызовы на **S'LGetData** или **S'LSetPos.**  
  
 При удалянии всех строк строк *(RowNumber* равен 0), приложение может предотвратить драйвер от удалять определенные строки с помощью массива работы строки, так же, как для операции обновления **S'LSetPos**. (См. [Обновление строк в Строке с помощью S'LSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения были заполнены путем извлечения и если массив состояния строки был сохранен, его значения в каждой из этих строк не должны быть SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.

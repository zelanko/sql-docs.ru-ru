---
title: Удаление строк в наборе строк с SQLSetPos | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 828ab8f154669473a6e90b60126d3b047c45e515
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Удаление строк в наборе строк с SQLSetPos
Операция удаления из **SQLSetPos** позволяет удалить один или несколько выбранных строк таблицы источника данных. Для удаления строк с **SQLSetPos**, приложение вызывает **SQLSetPos** с *операции* значение SQL_DELETE и *RowNumber* значение Номер строки для удаления. Если *RowNumber* равно 0, удаляются все строки в наборе строк.  
  
 После **SQLSetPos** возвращает удаленную строку текущей строки с состоянием SQL_ROW_DELETED. Строка не может использоваться в любой дальнейшей позиционированных операций, таких как вызовы **SQLGetData** или **SQLSetPos**.  
  
 При удалении всех строк набора строк (*RowNumber* равен 0), приложение может предотвратить удаление определенных строк с помощью массива операций строк, таким же образом, как и для операций обновления драйвера **SQLSetPos** . (См. [обновление строк в наборе строк с SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения заполняются выборкой и сохранено массив состояния строк, значения каждой из этих позиций строк необходимо SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.

---
title: Длина данных столбца | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8075358f3675b201a7b8b0528b08de305bf587da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="length-of-column-data"></a>Длина данных столбца
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров создает буфер, в кэше для каждого буфера длины и индикатора, привязанное к результирующий набор с **SQLBindCol**. Он использует значения в этих буферах для создания **ГДЕ** предложения, если он эмулирует позиционированного обновления или delete. Обновляет эти буферы из буферов набора строк при выборке данных из источника данных и при выполнении инструкции позиционированного обновления.  
  
 Если тип C буфера данных — SQL_C_CHAR и SQL_C_BINARY, а значение длины/индикатора равно SQL_NTS, длина строки данных помещается в буфер длины/индикатора.  
  
> [!NOTE]  
>  Библиотека курсоров не обновляет свой кэш для столбца, если **StrLen_or_IndPtr* в соответствующих строк буфера является значение SQL_DATA_AT_EXEC, ни результатом SQL_LEN_DATA_AT_EXEC макроса.

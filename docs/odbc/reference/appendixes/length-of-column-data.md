---
title: Длина данных столбца | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d2998eace4772624a1e6590ab2541577147f5c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041609"
---
# <a name="length-of-column-data"></a>Длина данных столбца
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Библиотека курсоров создает буфер в кэше для каждого буфера длины и индикатора, привязанный к результирующему набору с **SQLBindCol**. Он использует значения из этих буферов для создания **ГДЕ** предложение при эмулирует позиционированного обновления или удаления. Он обновляет эти буферы из буферов набора строк, когда этот метод извлекает данные из источника данных и при выполнении инструкций позиционированного обновления.  
  
 Если тип C буфера данных — SQL_C_CHAR и SQL_C_BINARY, а значение длины и индикатора равно SQL_NTS, длину строки данных помещаются в буфер длины/индикатора.  
  
> [!NOTE]  
>  Библиотека курсоров не обновляет свой кэш для столбца, если **StrLen_or_IndPtr* в соответствующих строк буфер имеет значение SQL_DATA_AT_EXEC, ни результатом SQL_LEN_DATA_AT_EXEC макроса.

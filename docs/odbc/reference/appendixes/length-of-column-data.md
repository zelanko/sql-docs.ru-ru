---
title: Длина данных колонки (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0b7ad515661cce4c5b1d407be768cc3da131bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304935"
---
# <a name="length-of-column-data"></a>Длина данных столбца
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсора создает буфер в кэше для каждого буфера длины/индикатора, привязанного к набору результатов с **s'LBindCol.** Он использует значения в этих буферах для построения положения **WHERE,** когда он эмулирует позиционируемое обновление или удаление инструкций. Он обновляет эти буферы из буферов строки, когда он получает данные из источника данных и когда он выполняет позиционированные операторы обновления.  
  
 Если тип C буфера данных SQL_C_CHAR или SQL_C_BINARY, а значение длины/индикатора SQL_NTS, длина строки данных вкладывается в буфер длины/индикатора.  
  
> [!NOTE]  
>  Библиотека курсора не обновляет свой кэш для столбца, если*StrLen_or_IndPtr* в соответствующем буфере набора строк SQL_DATA_AT_EXEC или результат омователя SQL_LEN_DATA_AT_EXEC.

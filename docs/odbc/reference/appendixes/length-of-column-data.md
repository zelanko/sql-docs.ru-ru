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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041609"
---
# <a name="length-of-column-data"></a>Длина данных столбца
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсоров создает буфер в кэше для каждого буфера длины или индикатора, привязанного к результирующему набору с помощью **SQLBindCol**. Он использует значения в этих буферах для создания предложения **WHERE** при эмуляции инструкций позиционированного обновления или удаления. Он обновляет эти буферы из буферов наборов строк, когда он извлекает данные из источника данных и когда он выполняет позиционированные инструкции UPDATE.  
  
 Если тип C буфера данных SQL_C_CHAR или SQL_C_BINARY, а значение длины/индикатора SQL_NTS, то длина строки данных помещается в буфер длины или индикатора.  
  
> [!NOTE]  
>  Библиотека курсоров не обновляет кэш для столбца, если **StrLen_or_IndPtr* в соответствующем буфере набора строк имеет SQL_DATA_AT_EXEC или результат макроса SQL_LEN_DATA_AT_EXEC.

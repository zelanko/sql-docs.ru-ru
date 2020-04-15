---
title: 'СЗЛ в C: Двоичный Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b0ce72f650e61b83ec99b0727752612d18da52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298831"
---
# <a name="sql-to-c-binary"></a>Преобразование данных из SQL в C: двоичные данные
Идентификаторами для двоичных типов данных ODBC S'L являются:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 В следующей таблице показаны типы данных ODBC C, в которые могут быть преобразованы двоичные данные S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Длина данных) \* 2 < *Буферная длина*<br /><br /> (Длина данных) \* 2 >- *Буферная длина*|Данные<br /><br /> Truncated данные|Длина данных в байтах<br /><br /> Длина данных в байтах|Недоступно<br /><br /> 01004|  
|SQL_C_WCHAR|(Длина данных) \* 2 < *Буферная длина*<br /><br /> (Длина данных) \* 2 >- *Буферная длина*|Данные<br /><br /> Truncated данные|Длина данных в символах<br /><br /> Длина данных в символах|Недоступно<br /><br /> 01004|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Truncated данные|Длина данных в байтах<br /><br /> Длина данных в байтах|Недоступно<br /><br /> 01004|  
  
 При преобразовании двоичных данных S'L в данные персонажа C каждый байт (8 бит) исходных данных представлен как два символа ASCII. Эти символы представляют собой представление персонажа ASCII номера в его гексадецимальной форме. Например, двоичный 00000001 преобразуется в "01", а двоичный 11111111 преобразуется в "FF".  
  
 Водитель всегда преобразует отдельные байты в пары гексадецичных цифр и завершает строку персонажа с нулевым байтом. Из-за этого, если *BufferLength* четвонна и меньше, чем длина преобразованных данных, последний байт буфера*TargetValuePtr* не используется. (Преобразованные данные требуют четного количества байтов, предпоследний байт является нулевым байтом, а последний байт не может быть использован.)  
  
> [!NOTE]  
>  Разработчики приложений не рекомендуется связывать двоичные данные S'L с типом данных символа C. Это преобразование, как правило, неэффективно и медленно.

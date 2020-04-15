---
title: Картирование саЗЛКолАтрибуты (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c2c8386d6771141eaa0145a5d5964d70d6084d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305420"
---
# <a name="sqlcolattributes-mapping"></a>Сопоставление SQLColAttributes
Когда приложение вызывает **S'LColAttributes** через драйвер ODBC *3.x,* вызов в **S'LColAttributes** отображается на **s'LColAttributes** следующим образом:  
  
> [!NOTE]
>  Префикс, используемый в значениях *FieldIdentifier* в ODBC *3.x,* был изменен с той, которая используется в ODBC *2.x*. Новая приставка "SQL_DESC"; старая приставка была "SQL_COLUMN".  
  
1.  Если приложение является приложением ODBC *2.x,* *fDescType* SQL_COLUMN_TYPE, а возвращенный тип представляет собой краткий тип DATETIME, менеджер драйвера отображает значения возврата для кода даты, времени и метки времени.  
  
2.  Если *fDescType* является SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE или SQL_COLUMN_COUNT, менеджер драйвера вызывает **s'LColAttribute** в драйвере с аргументом *FieldIdentifier,* отображаемым в SQL_DESC_NAME, SQL_DESC_NULLABLE или SQL_DESC_COUNT, по мере необходимости.*.* Все остальные значения *fDescType* передаются водителю.  
  
 Водитель ODBC *3.x* должен поддерживать все ODBC *3.x* *FieldIdentifiers,* перечисленные для **S'LColAttribute**.  
  
 Водитель ODBC *3.x* должен поддерживать SQL_COLUMN_PRECISION и SQL_DESC_PRECISION, SQL_COLUMN_SCALE и SQL_DESC_SCALE, а также SQL_COLUMN_LENGTH и SQL_DESC_LENGTH. Эти значения отличаются, потому что точность, масштаб и длина определяются по-разному в ODBC *3.x,* чем они были в ODBC *2.x*. Для получения дополнительной информации в приложении D: Типы данных [см.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)

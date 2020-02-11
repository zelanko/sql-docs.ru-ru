---
title: Сопоставление SQLColAttributes | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08abd0128a6fa2a478af0e9dc9c292ff973ace79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064492"
---
# <a name="sqlcolattributes-mapping"></a>Сопоставление SQLColAttributes
Когда приложение вызывает **SQLColAttributes** через драйвер ODBC *3. x* , вызов **SQLColAttributes** сопоставляется с **SQLColAttribute** следующим образом:  
  
> [!NOTE]
>  Префикс, используемый в значениях *фиелдидентифиер* в ODBC *3. x* , был изменен с помощью ODBC *2. x*. Новый префикс — "SQL_DESC"; Старый префикс — "SQL_COLUMN".  
  
1.  Если приложение является приложением ODBC *2. x* , *фдесктипе* имеет SQL_COLUMN_TYPE, а возвращаемый тип является кратким типом DateTime, диспетчер драйверов сопоставляет возвращаемые значения для кодов даты, времени и отметки времени.  
  
2.  Если *фдесктипе* имеет значение SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE или SQL_COLUMN_COUNT, диспетчер драйверов вызывает **SQLColAttribute** в драйвере с аргументом *фиелдидентифиер* , сопоставленным с SQL_DESC_NAME, SQL_DESC_NULLABLE или SQL_DESC_COUNT, в зависимости от ситуации *.* Все остальные значения *фдесктипе* передаются в драйвер.  
  
 Драйвер ODBC *3. x* должен поддерживать все *фиелдидентифиерс* ODBC *3. x* , перечисленные для **SQLColAttribute**.  
  
 Драйвер ODBC *3. x* должен поддерживать SQL_COLUMN_PRECISION и SQL_DESC_PRECISION, SQL_COLUMN_SCALE и SQL_DESC_SCALE, а SQL_COLUMN_LENGTH и SQL_DESC_LENGTH. Эти значения отличаются, поскольку точность, масштаб и длина определяются по-разному в ODBC *3. x* , чем в ODBC *2. x*. Дополнительные сведения см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.

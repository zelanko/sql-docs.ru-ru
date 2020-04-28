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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c2c8386d6771141eaa0145a5d5964d70d6084d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305420"
---
# <a name="sqlcolattributes-mapping"></a>Сопоставление SQLColAttributes
Когда приложение вызывает **SQLColAttributes** через драйвер ODBC *3. x* , вызов **SQLColAttributes** сопоставляется с **SQLColAttribute** следующим образом:  
  
> [!NOTE]
>  Префикс, используемый в значениях *фиелдидентифиер* в ODBC *3. x* , был изменен с помощью ODBC *2. x*. Новый префикс — "SQL_DESC"; Старый префикс — "SQL_COLUMN".  
  
1.  Если приложение является приложением ODBC *2. x* , *фдесктипе* имеет SQL_COLUMN_TYPE, а возвращаемый тип является кратким типом DateTime, диспетчер драйверов сопоставляет возвращаемые значения для кодов даты, времени и отметки времени.  
  
2.  Если *фдесктипе* имеет значение SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE или SQL_COLUMN_COUNT, диспетчер драйверов вызывает **SQLColAttribute** в драйвере с аргументом *фиелдидентифиер* , сопоставленным с SQL_DESC_NAME, SQL_DESC_NULLABLE или SQL_DESC_COUNT, в зависимости от ситуации *.* Все остальные значения *фдесктипе* передаются в драйвер.  
  
 Драйвер ODBC *3. x* должен поддерживать все *фиелдидентифиерс* ODBC *3. x* , перечисленные для **SQLColAttribute**.  
  
 Драйвер ODBC *3. x* должен поддерживать SQL_COLUMN_PRECISION и SQL_DESC_PRECISION, SQL_COLUMN_SCALE и SQL_DESC_SCALE, а SQL_COLUMN_LENGTH и SQL_DESC_LENGTH. Эти значения отличаются, поскольку точность, масштаб и длина определяются по-разному в ODBC *3. x* , чем в ODBC *2. x*. Дополнительные сведения см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.

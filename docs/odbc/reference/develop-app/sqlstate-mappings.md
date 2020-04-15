---
title: Картирование СЗЛСТАТ (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec58c0e41869529bbba5fd31ad534976923a990d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299744"
---
# <a name="sqlstate-mappings"></a>Сопоставления SQLSTATE
В этой теме обсуждаются значения S'LSTATE для ODBC *2.x* и ODBC *3.x*. Для получения более подробной информации о значениях ODBC *3.x* S'LSTATE [см.](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)  
  
 В ODBC *3.x*, HYxxx S'LSTATEs возвращаются вместо S1xxx, а 42Sxx S'LSTATEs возвращаются вместо S00XX. Это было сделано для согласования со стандартами Open Group и ISO. Во многих случаях отображение не является единственным, поскольку стандарты переопределили толкование нескольких СЗЛСТАТ.  
  
 При обновлении приложения ODBC *2.x* до приложения ODBC *3.x* приложение должно быть изменено, чтобы ожидать, что ODBC *3.x* S'LSTATEs вместо ODBC *2.x* S'LSTATEs. В следующей таблице перечислены ODBC *3.x* S'LSTATEs, на которые отображается каждый ODBC *2.x* S'LSTATE.  
  
 Когда атрибут среды SQL_ATTR_ODBC_VERSION установлен на SQL_OV_ODBC2, драйвер публикует ODBC *2.x* S'LSTATE вместо ODBC *3.x* S'LSTATEs, когда называется **S'LGetDiagField** или **S'LGetDiagRec.** Конкретное отображение может быть определено, заметив ODBC *2.x* S'LSTATE в колонке 1 из следующей таблицы, которая соответствует ODBC *3.x* S'LSTATE в колонке 2.  
  
|ODBC *2.x* S'Lstate|ODBC *3.x* S'Lstate|Комментарии|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24 000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC *2.x* S'Lstate S1002 отображается на отображении ODBC *3.x* S'Lstate 07009, если основная функция — **S'LBindCol,** **S'LColAttribute,** **S'LExtendedFetch**, **S'LFetch,** **S'LFetchScroll**, или **S'LGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Возвращается для недействительного использования нулевого указателя.|  
|S1009|HY024|Возвращается для значения недействительных атрибутов.|  
|S1009|HY092|Возвращается для обновления или удаляния данных по вызову в **S'LSetPos,** или добавлению, обновлению или удалянию данных по вызову в **S'LBulkOperations,** когда валюта читается только по телефону.|  
|S1010|HY007 HY010|S'LSTATE S1010 отображается на карте s'LSTATE HY007, когда **s'LDescribeCol** называется до вызова **S'LPrepare**, **S'LExecDirect**, или функции каталога для *StatementHandle*. В противном случае, S'LSTATE S1010 отображается на карте s'LSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3.x* S'Lstate 07009 отображается на ODBC *2.x* S'Lstate S1093, если основная функция **s'LBindParameter** или **S'LDescribeParam**.|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC *3.x* S'Lstate 07008 отображается на ODBC *2.x* S'Lstate S1000.

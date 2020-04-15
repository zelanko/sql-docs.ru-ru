---
title: Написание ODBC 3.x Драйверы Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62f2a701fd5ac94c92d41494a4fd1ab023edaf25
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300364"
---
# <a name="writing-odbc-3x-drivers"></a>Написание драйверов ODBC 3.x
В следующей таблице отображается поддержка функций в ODBC 3. *x* драйвер и приложение ODBC, а также отображение, выполняемые менеджером драйвера, когда функции вызваны против ODBC 3. *x* драйвер.  
  
|Компонент|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> Драйвер?|Поддерживается<br /><br /> по<br /><br /> ODBC 3. *x*<br /><br /> Приложения?|Карта/поддержка<br /><br /> ODBC 3. *x*<br /><br /> Менеджер драйвера для<br /><br /> ODBC 3. *x* водитель?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**СЗЛАллокКоннект**|нет|Нет, нет|Да|  
|**СЗЛАллокЕнв**|нет|Нет, нет|Да|  
|**СЗЛАллокХэндл**|Да|Да|нет|  
|**СЗЛАлокСтмт**|нет|Нет, нет|Да|  
|**SQLBindCol**|Да|Да|нет|  
|**СЗЛБиндпарам**|нет|Да, да|Да|  
|**SQLBindParameter**|Да|Да|нет|  
|**SQLBrowseConnect**|Да|Да|нет|  
|**СЗЛБалКОперации**|Да|Да|нет|  
|**SQLCancel**|Да|Да|нет|  
|**SQLCloseCursor**|Да|Да|нет|  
|**SQLColAttribute**|Да|Да|нет|  
|**СЗЛКолАтрибуты**|Нет, нет|нет|Да|  
|**SQLColumnPrivileges**|Да|Да|нет|  
|**SQLColumns**|Да|Да|нет|  
|**SQLConnect**|Да|Да|нет|  
|**СЗЛКопиДеск**|Да|Да|Да,|  
|**Источники данных S'LData**|нет|Да|Да|  
|**SQLDescribeCol**|Да|Да|нет|  
|**SQLDescribeParam**|Да|Да|нет|  
|**СЗЛДИСКоннект**|Да|Да|нет|  
|**SQLDriverConnect**|Да|Да|нет|  
|**SQLDrivers**|нет|Да|Да|  
|**SQLEndTran**|Да|Да|нет|  
|**Sqlerror**|нет|Нет, нет|Да|  
|**SQLExecDirect**|Да|Да|нет|  
|**SQLExecute**|Да|Да|нет|  
|**Sqlextendedfetch**|Да|нет|нет|  
|**SQLFetch**|Да|Да|нет|  
|**SQLFetchScroll**|Да|Да|нет|  
|**SQLForeignKeys**|Да|Да|нет|  
|**СЗЛФриКоннект**|нет|Да,|Да|  
|**СЗЛФриЕнв**|нет|Да,|Да|  
|**SQLFreeHandle**|Да|Да|нет|  
|**Функция SQLFreeStmt**|Да|Да|нет|  
|**SQLGetConnectAttr**|Да|Да|нет|  
|**СЗЛГетКоннектОпция**|Нет, no|Нет, нет|Да|  
|**SQLGetCursorName**|Да|Да|нет|  
|**SQLGetData**|Да|Да|нет|  
|**SQLGetDescField**|Да|Да|нет|  
|**SQLGetDescRec**|Да|Да|нет|  
|**SQLGetDiagField**|Да|Да|нет|  
|**Функции SQLGetDiagRec**|Да|Да|нет|  
|**СЗЛГетЕнвТтр**|Да|Да|нет|  
|**SQLGetFunctions**|Нет, no|Да|Да|  
|**SQLGetInfo**|Да|Да|нет|  
|**SQLGetStmtAttr**|Да|Да|нет|  
|**СЗЛГетСтмтOption**|Нет, no|Нет, нет|Да|  
|**SQLGetTypeInfo**|Да|Да|нет|  
|**SQLMoreResults**|Да|Да|нет|  
|**SQLNativeSql**|Да|Да|нет|  
|**SQLNumParams**|Да|Да|нет|  
|**SQLNumResultCols**|Да|Да|нет|  
|**SQLParamData**|Да|Да|нет|  
|**СЗЛПарамОпции**|нет|нет|Да|  
|**SQLPrepare**|Да|Да|нет|  
|**SQLPrimaryKeys**|Да|Да|нет|  
|**SQLProcedureColumns**|Да|Да|нет|  
|**SQLProcedures**|Да|Да|нет|  
|**SQLPutData**|Да|Да|нет|  
|**SQLRowCount**|Да|Да|нет|  
|**SQLSetConnectAttr**|Да|Да|нет|  
|**СЗЛЕтКоннектОпция**|Нет, no|Нет, нет|Да|  
|**СЗЛСетКурсОрНамейм**|Да|Да|нет|  
|**SQLSetDescField**|Да|Да|нет|  
|**SQLSetDescRec**|Да|Да|нет|  
|**SQLSetEnvAttr**|Да|Да|нет|  
|**функция SQLSetPos;**|Да|Да|нет|  
|**СЗЛСетПарам**|нет|нет|Да|  
|**СЗЛСетПрокрутОпция**|Да|Да|нет|  
|**SQLSetStmtAttr**|Да|Да|нет|  
|**СЗЛСетСтмтOption**|Нет, no|Нет, нет|Да|  
|**SQLSpecialColumns**|Да|Да|нет|  
|**SQLStatistics**|Да|Да|нет|  
|**SQLTablePrivileges**|Да|Да|нет|  
|**SQLTables**|Да|Да|нет|  
|**СЗЛТрансакт**|нет|Нет, нет|Да|  
  
 Эта функция унижается в ODBC 3. *x*. ODBC 3. *приложения x* не должны использовать эту функцию. Тем не менее, приложение Open Group или ISO CLI может вызвать эту функцию.  
  
 ODBC 3. *приложения x* должны использовать **вместо** **S'LBindParam.** Тем не менее, приложение Open Group или ISO CLI может вызвать эту функцию.  
  
 Авторы драйверов должны отметить, что ODBC 2. *x* атрибуты столбца SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE и SQL_COLUMN_LENGTH должны поддерживаться с **помощью s'LColAttribute**.  
  
 **При** копировании дескриптора по соединениям, принадлежащим различным драйверам, частично реализуется менеджером драйверов. Водители обязаны поддерживать **S'LCopyDesc** через два своих собственных соединений. Такие функции, как **S'LDrivers,** которые реализуются исключительно менеджером драйверов, не отображаются в этом списке.  
  
 При определенных обстоятельствах водителям может потребоваться поддерживать эту функцию. Для получения дополнительной информации смотрите справочную страницу этой функции.  
  
 Водитель может выбрать поддержку **S'LGetFunctions,** если набор функций, поддерживаемых драйвером, варьируется от подключения к подключению.

---
title: Поддерживаемая модель Cursor (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cf3400f24e20a8fa864404612bf07ea44efce49e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301130"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель курсоров (драйвер ODBC для Visual FoxPro)
Визуальный драйвер FoxPro ODBC поддерживает как *блок* *(rowset)* и *статические* курсоры. Статические курсоры поддерживаются для любого драйвера, который соответствует соответствию ODBC уровня 1. Драйвер не поддерживает динамические, клавишные или смешанные (ключевые и динамические) курсоры.  
  
 Ваше приложение может вызвать [s'LSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с SQL_CURSOR_TYPE вариантом SQL_CURSOR_FORWARD_ONLY (блок курсор) или SQL_CURSOR_STATIC (статический курсор).  
  
> [!NOTE]  
>  Если вы позвоните по **телефону s'LSetStmtOption** с SQL_CURSOR_TYPE опцией, не SQL_CURSOR_FORWARD_ONLY или SQL_CURSOR_STATIC, функция возвращается SQL_SUCCESS_WITH_INFO с S'LSTATE 01S02 (изменение стоимости опциона). Водитель устанавливает все неподдерживаемые режимы курсора для SQL_CURSOR_STATIC.  
  
 Для получения более подробной информации о типах курсоров и о **S'LSetStmtOption**см. [ODBC Programmer's Reference](../../odbc/reference/odbc-programmer-s-reference.md)  
  
## <a name="block-cursor"></a>блочный курсор  
 Набор результатов с пересчетом только для чтения возвращается клиенту, который отвечает за хранение данных.  
  
## <a name="static-cursor"></a>статический курсор  
 Снимок набора данных, определяемого запросом. Статические курсоры не отражают изменения базовых данных другими пользователями в реальном времени. Буфер памяти курсора поддерживается библиотекой курсора ODBC, которая позволяет прокручивать вперед и назад.  
  
## <a name="rowset"></a>набор строк  
 Блоки данных, хранящихся в курсоре, представляющие строки, извлеченные из источника данных.

---
title: Поддерживаемая модель курсора (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301130"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель курсоров (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает как *блок* (*набор строк*), так и *статические* курсоры. Статические курсоры поддерживаются для любого драйвера, который соответствует требованиям ODBC уровня 1. Драйвер не поддерживает динамические курсоры, управляемые набором ключей или смешанные (с ключевым набором ключей и динамические).  
  
 Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY (блочный курсор) или SQL_CURSOR_STATIC (статический курсор).  
  
> [!NOTE]  
>  При вызове **SQLSetStmtOption** с параметром SQL_CURSOR_TYPE, отличным от SQL_CURSOR_FORWARD_ONLY или SQL_CURSOR_STATIC, функция возвращает SQL_SUCCESS_WITH_INFO со значением SQLState 01S02 (значение параметра изменено). Драйвер устанавливает для всех неподдерживаемых режимов курсора значение SQL_CURSOR_STATIC.  
  
 Дополнительные сведения о типах курсоров и о **SQLSetStmtOption**см. в [справочнике программиста по ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>блочный курсор  
 Результирующий набор, предназначенный только для чтения и пересылаемый клиенту, который отвечает за поддержание хранилища данных.  
  
## <a name="static-cursor"></a>статический курсор  
 Моментальный снимок набора данных, определенного запросом. Статические курсоры не отображают изменения базовых данных в реальном времени другими пользователями. Буфер памяти курсора сохраняется библиотекой курсоров ODBC, которая позволяет выполнять прямую и обратную прокрутку.  
  
## <a name="rowset"></a>набор строк  
 Блоки данных, хранящиеся в курсоре, представляющие собой строки, полученные из источника данных.

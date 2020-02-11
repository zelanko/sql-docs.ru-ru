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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e623c0ce5135a4b2e558be9c405ec2757e605ceb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080712"
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

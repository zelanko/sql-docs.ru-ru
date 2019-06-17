---
title: Поддерживается модель курсоров (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 875348a501c292e55b267ece769f16dd6bc9dbdd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270935"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель курсоров (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает как *блок* (*набора строк*) и *статический* курсоров. Статические курсоры поддерживаются для любой драйвер, который соответствует ODBC 1 уровень соответствия. Драйвер не поддерживает динамические, управляемые набором ключей или смешанная (keyset и dynamic) курсоров.  
  
 Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY (блочного курсора) или SQL_CURSOR_STATIC (статического курсора).  
  
> [!NOTE]  
>  При вызове метода **SQLSetStmtOption** SQL_CURSOR_TYPE параметр, отличный от SQL_CURSOR_FORWARD_ONLY или SQL_CURSOR_STATIC, функция возвращает значение SQL_SUCCESS_WITH_INFO с SQLSTATE 01S02 (значение параметра изменено). Драйвер устанавливает все режимы неподдерживаемый курсора SQL_CURSOR_STATIC.  
  
 Дополнительные сведения о типах курсоров и около **SQLSetStmtOption**, см. в разделе [Справочник по программированию ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>блочный курсор  
 Прокрутка вперед, только для чтения результирующего набора, возвращаемого клиенту, кто отвечает за обслуживание хранилища данных.  
  
## <a name="static-cursor"></a>статический курсор  
 Моментальный снимок набор данных, определенным в запросе. Статические курсоры не отражают в режиме реального времени изменения базовых данных другими пользователями. Буфер памяти курсора поддерживается библиотекой курсоров ODBC, который позволяет прокрутку вперед и назад.  
  
## <a name="rowset"></a>набор строк  
 Блоки данных, хранящихся в курсоре, представляющий строки, полученные из источника данных.

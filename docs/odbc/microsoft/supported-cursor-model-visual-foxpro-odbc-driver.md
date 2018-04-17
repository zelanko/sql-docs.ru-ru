---
title: Поддерживается модель курсора (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13f8c22a9c47fd4e0d83fdb7bb73ff12f8e96e93
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Модель поддерживаемых курсоров (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает как *блок* (*строк*) и *статических* курсоров. Статические курсоры поддерживаются для любой драйвер, который соответствует на соответствие требованиям ODBC уровня 1. Драйвер не поддерживает динамические, управляемые набором ключей или смешанных (управляемые набором ключей и динамические) курсоров.  
  
 Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY (блочного курсора) или SQL_CURSOR_STATIC (статического курсора).  
  
> [!NOTE]  
>  При вызове метода **SQLSetStmtOption** SQL_CURSOR_TYPE параметр, отличный от SQL_CURSOR_FORWARD_ONLY или SQL_CURSOR_STATIC, функция возвращает значение SQL_SUCCESS_WITH_INFO с SQLSTATE 01S02 (значение параметра изменено). Драйвер устанавливает для всех режимов неподдерживаемый курсора SQL_CURSOR_STATIC.  
  
 Дополнительные сведения о типах курсоров и о **SQLSetStmtOption**, в разделе [справочнике программиста ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>блочный курсор  
 Прокрутка вперед, только для чтения результирующего набора, возвращаемого клиенту, который отвечает за поддержание хранения данных.  
  
## <a name="static-cursor"></a>статический курсор  
 Моментальный снимок, определенным в запросе набора данных. Статические курсоры не отражают изменений в реальном времени базовых данных другими пользователями. Буфер памяти курсора поддерживается всеми библиотеку курсоров ODBC позволяет прямой и обратной прокрутки.  
  
## <a name="rowset"></a>набор строк  
 Блоки данных, хранящихся в курсоре, представляющий строки, полученные из источника данных.

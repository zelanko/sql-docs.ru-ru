---
title: Переходы дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 027b711c5c1a2cb2d35e65efdc2b00f441841d8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240978"
---
# <a name="descriptor-transitions"></a>Переходы дескрипторов
Дескрипторы ODBC имеет три состояния.  
  
|Штат|Описание|  
|-----------|-----------------|  
|D0|Нераспределенное дескриптора|  
|D1i|Неявно выделенные дескриптора|  
|D1e|Явно выделенные дескриптора|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние дескриптора.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e [2]|--|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH) [2]|(HY017)|D0|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField и SQLGetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField и SQLSetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH) [1]|--|--|  
  
 [1] в этой строке показаны переходы при *DescriptorHandle* был дескриптор Отменить, APD или IPD, или (для **SQLSetDescField**) при *DescriptorHandle* был дескриптор IRD и *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR или SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявные|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--|--|--|

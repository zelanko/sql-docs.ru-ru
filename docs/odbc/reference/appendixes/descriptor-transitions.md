---
title: "Дескриптор переходов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 280d35d8ce03d3d7685441c12d99c05c9ff5f451
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-transitions"></a>Дескриптор переходов
Дескрипторы ODBC имеет три состояния.  
  
|Состояние|Description|  
|-----------|-----------------|  
|D0|Незанятое дескриптора|  
|D1i|Неявно выделенного дескриптора.|  
|D1e|Явно выделенного дескриптора.|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние дескриптора.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(СИСТЕМЫ) [2]|(HY017)|D0|  
  
 [1] в этой строке показаны переходы при *HandleType* был значение SQL_HANDLE_STMT.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>Функция SQLGetDescField и SQLGetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField и SQLSetDescRec  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(СИСТЕМЫ) [1]|--|--|  
  
 [1] в этой строке показаны переходы при *DescriptorHandle* было Отменить, APD или IPD, дескриптор или (для **SQLSetDescField**) при *DescriptorHandle* был дескриптор IRD и *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR или SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--|--|--|

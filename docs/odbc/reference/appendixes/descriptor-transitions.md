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
ms.openlocfilehash: 44e9d92c7371451d6bfdd2e1513c3f8fdac8447b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129999"
---
# <a name="descriptor-transitions"></a>Переходы дескрипторов
Дескрипторы ODBC имеют следующие три состояния.  
  
|State|Description|  
|-----------|-----------------|  
|Состояния|Нераспределенный дескриптор|  
|D1i|Неявно выделенный дескриптор|  
|D1e|Явно выделенный дескриптор|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние дескриптора.  
  
## <a name="sqlallochandle"></a>Функцию SQLAllocHandle  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_STMT.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>склкопидеск  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--[1]|Состояния|--|  
|IH открыт|(HY017)|Состояния|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_STMT.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField и SQLGetDescRec  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField и SQLSetDescRec  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|IH одного|--|--|  
  
 [1] в этой строке отображаются переходы, если *дескрипторхандле* является маркером АРД, APD или IPD или (для **SQLSetDescField**), когда *дескрипторхандле* был создан маркер IRD, а *фиелдидентифиер* — SQL_DESC_ARRAY_STATUS_PTR или SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|Состояния<br /><br /> Не выделено|D1i<br /><br /> Неявный|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--|--|--|

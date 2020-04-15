---
title: Дескриптор Переходы (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec5c26bdde8a0d470f2d93e753504bf1c51edcc0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307045"
---
# <a name="descriptor-transitions"></a>Переходы дескрипторов
Дескрипторы ODBC имеют следующие три состояния.  
  
|Состояние|Описание|  
|-----------|-----------------|  
|D0|Нераспределенный дескриптор|  
|D1i|Неявно выделенный дескриптор|  
|D1e|Явно выделенный дескриптор|  
  
 Следующие таблицы показывают, как каждая функция ODBC влияет на состояние дескриптора.  
  
## <a name="sqlallochandle"></a>СЗЛАллокХэндл  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|D1i|--|--|  
|D1e|--|--|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_STMT.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>СЗЛКопиДеск  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH) [2]|(HY017)|D0|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_STMT.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>СЗЛГетДескФилд и СЗЛГетДескРе  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>СЗЛСетДескФилд и СЗЛСетДеск  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|(IH) [1]|--|--|  
  
 В этой строке показаны переходы, когда *DescriptorHandle* был ручкой ARD, APD или IPD, или (для **S'LSetDescField),** когда *DescriptorHandle* был ручкой IRD, а *FieldIdentifier* был SQL_DESC_ARRAY_STATUS_PTR или SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|D0<br /><br /> Не выделено|D1i<br /><br /> Неявно|D1e<br /><br /> Явно|  
|------------------------|----------------------|----------------------|  
|--|--|--|

---
title: "SQLBindParameter (библиотека курсоров) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 45b3a0355edb0c9fbd37f7047aa0a1e6ff9a1fe8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLBindParameter** функции в библиотеку курсоров. Общие сведения о **SQLBindParameter**, в разделе [SQLBindParameter, функция](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Приложение может вызвать **SQLBindParameter** для повторной привязки параметров, при условии, что тип данных C, размер столбца и десятичные цифры из присоединенного столбца остаются неизменными.  
  
 Библиотека курсоров поддерживает настройку атрибута инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR для использования привязки смещения. (**SQLBindParameter** не должен вызываться для этой привязки происходят.)  
  
 Библиотека курсоров поддерживает параметры привязки данных времени выполнения.


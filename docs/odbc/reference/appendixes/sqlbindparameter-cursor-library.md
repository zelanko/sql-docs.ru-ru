---
title: SQLBindParameter (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eafab0f29cb4e1b7ecdfea378f9315ba29cf133f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813672"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLBindParameter** функции в библиотеку курсоров. Общие сведения о **SQLBindParameter**, см. в разделе [функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Приложение может вызвать **SQLBindParameter** выполнять повторную привязку параметров, до тех пор, пока тип данных C, размер столбца и десятичные цифры из присоединенного столбца не изменяются.  
  
 Библиотека курсоров поддерживает задание SQL_ATTR_ROW_BIND_OFFSET_PTR атрибут инструкции для использования привязки смещения. (**SQLBindParameter** не обязательно должен вызываться для этой привязки возможно.)  
  
 Библиотека курсоров поддерживает параметры привязки данных во время выполнения.

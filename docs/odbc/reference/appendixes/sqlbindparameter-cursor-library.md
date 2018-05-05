---
title: SQLBindParameter (библиотека курсоров) | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d20324c0d7366573600aa460e3c062a01fd2cc4e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLBindParameter** функции в библиотеку курсоров. Общие сведения о **SQLBindParameter**, в разделе [SQLBindParameter, функция](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Приложение может вызвать **SQLBindParameter** для повторной привязки параметров, при условии, что тип данных C, размер столбца и десятичные цифры из присоединенного столбца остаются неизменными.  
  
 Библиотека курсоров поддерживает настройку атрибута инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR для использования привязки смещения. (**SQLBindParameter** не должен вызываться для этой привязки происходят.)  
  
 Библиотека курсоров поддерживает параметры привязки данных времени выполнения.

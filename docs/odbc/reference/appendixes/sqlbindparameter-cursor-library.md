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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55708cc5192fb40149d6db7710f6ee638c4880d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305432"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLBindParameter** в библиотеке курсоров. Общие сведения о **SQLBindParameter**см. в разделе [функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Приложение может вызвать **SQLBindParameter** для повторной привязки параметров при условии, что тип данных C, размер столбца и десятичные разряды привязанного столбца остаются неизменными.  
  
 Библиотека курсоров поддерживает установку атрибута SQL_ATTR_ROW_BIND_OFFSET_PTR инструкции для использования смещений привязки. (Для выполнения этой повторной привязки не требуется вызывать**SQLBindParameter** .)  
  
 Библиотека курсоров поддерживает привязку параметров данных при выполнении.

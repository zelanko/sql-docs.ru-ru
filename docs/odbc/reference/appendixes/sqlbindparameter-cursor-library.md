---
title: СЗЛБиндПараст (Библиотека Курсора) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305432"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LBindParameter** в библиотеке курсоров. Для получения общей информации о **функции S'LBindParameter** [см.](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
 Приложение может вызывать **s'LBindParameter** для пересвязывания параметров, если тип данных C, размер столбца и десятичные цифры связанного столбца остаются неизменными.  
  
 Библиотека курсора поддерживает установку атрибута SQL_ATTR_ROW_BIND_OFFSET_PTR оператора для использования связывающих смещений. (**S'LBindParameter** не должны быть вызваны для этого повторного происходит.)  
  
 Библиотека курсора поддерживает обязательные параметры данных при выполнении.

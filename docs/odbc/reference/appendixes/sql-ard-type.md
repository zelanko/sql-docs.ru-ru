---
title: SQL_ARD_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 802040851259a8537fabcd3cc0da1afdf9b8dbe0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057054"
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
Идентификатор типа SQL_ARD_TYPE используется для указания, что данные в буфере будут иметь тип, указанный в поле SQL_DESC_CONCISE_TYPE Отменить. SQL_ARD_TYPE вводится в *TargetType* аргумент для вызова **SQLGetData** вместо определенный тип данных и позволяет приложению изменять данные типа буфера, изменив дескриптор поле. Это значение связывает тип данных  *\*TargetValuePtr* буфер для поля дескриптора. (SQL_ARD_TYPE не введен в вызов **SQLBindCol** или **SQLBindParameter** так, как тип привязанного буфера уже привязан к полям SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE и может быть изменено в любое время, изменив одно из этих полей.)  
  
 Идентификатор типа SQL_ARD_TYPE позволяют указать нестандартные значения для ведущих точности и секунды значения типа интервальных типов данных и точность и масштаб значения для данных SQL_C_NUMERIC типа. Дополнительные сведения см. в разделе [переопределение по умолчанию начальные и точность секунды для интервальных типов данных](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) и [переопределение по умолчанию точность и масштаб для числовых типов данных](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)далее в этом приложении.

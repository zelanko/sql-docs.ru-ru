---
title: "SQL_ARD_TYPE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c789c560adbb01d4c9c0bd2700dd3d1b0757f04
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
Идентификатор типа SQL_ARD_TYPE используется для указания, что данные в буфере будут иметь тип, указанный в поле SQL_DESC_CONCISE_TYPE Отменить. Вводится SQL_ARD_TYPE *TargetType* аргумент для вызова **SQLGetData** вместо определенный тип данных и позволяет приложению изменять данные типа буфера, изменив дескриптора поле. Это значение связывает тип данных  *\*TargetValuePtr* буфер для поля дескриптора. (SQL_ARD_TYPE данные не будут сохранены при обращении к **SQLBindCol** или **SQLBindParameter** , так как тип привязанного буфера уже привязан к полям SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE и может быть изменено в любое время, изменив одно из этих полей.)  
  
 Идентификатор типа SQL_ARD_TYPE можно указать нестандартные значения для начальных точность и интервальных типов данных точность секунд и точность и масштаб значения для данных SQL_C_NUMERIC типа. Дополнительные сведения см. в разделе [переопределение по умолчанию начальные и точность секунд для типа данных Interval](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) и [переопределение по умолчанию точность и масштаб для числовых типов данных](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)далее в этом приложении.

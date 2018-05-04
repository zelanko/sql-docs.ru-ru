---
title: SQL_ARD_TYPE | Документы Microsoft
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9e02377c4f192e9cbf5f6a41ab62ef5345ba4ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlardtype"></a>SQL_ARD_TYPE
Идентификатор типа SQL_ARD_TYPE используется для указания, что данные в буфере будут иметь тип, указанный в поле SQL_DESC_CONCISE_TYPE Отменить. Вводится SQL_ARD_TYPE *TargetType* аргумент для вызова **SQLGetData** вместо определенный тип данных и позволяет приложению изменять данные типа буфера, изменив дескриптора поле. Это значение связывает тип данных  *\*TargetValuePtr* буфер для поля дескриптора. (SQL_ARD_TYPE данные не будут сохранены при обращении к **SQLBindCol** или **SQLBindParameter** , так как тип привязанного буфера уже привязан к полям SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE и может быть изменено в любое время, изменив одно из этих полей.)  
  
 Идентификатор типа SQL_ARD_TYPE можно указать нестандартные значения для начальных точность и интервальных типов данных точность секунд и точность и масштаб значения для данных SQL_C_NUMERIC типа. Дополнительные сведения см. в разделе [переопределение по умолчанию начальные и точность секунд для типа данных Interval](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) и [переопределение по умолчанию точность и масштаб для числовых типов данных](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)далее в этом приложении.

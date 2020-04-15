---
title: SQL_ARD_TYPE Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7e28d6babb7db8364697ae62092256396b44914
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305035"
---
# <a name="sql_ard_type"></a>SQL_ARD_TYPE
Идентификатор типа SQL_ARD_TYPE используется для указания на то, что данные в буфере будут типа, указанного в SQL_DESC_CONCISE_TYPE поле ARD. SQL_ARD_TYPE вводится в аргумент *TargetType* вызова на **S'LGetData** вместо конкретного типа данных и позволяет приложению изменять тип данных буфера, изменяя поле дескриптора. Это значение связывает тип данных буфера * \*TargetValuePtr* с полем дескриптора. (SQL_ARD_TYPE не вводится в вызов на **S'LBindCol** или **S'LBindParameter,** потому что тип связанного буфера уже привязан к SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE полям и может быть изменен в любое время, изменив любое из этих полей.)  
  
 Идентификатор типа SQL_ARD_TYPE может использоваться для определения значений недефолтов для ведущей точности и секундной точности типов интервальных данных, а также значений точности и масштаба для SQL_C_NUMERIC типа данных. Для получения дополнительной информации, [см. Переопределение ведущих по умолчанию и секунд точности для интервала типов данных](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) и [преобладающие точности по умолчанию и масштабирования для численных типов данных](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md), позже в этом приложении.

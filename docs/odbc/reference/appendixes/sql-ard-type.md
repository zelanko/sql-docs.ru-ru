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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7e28d6babb7db8364697ae62092256396b44914
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305035"
---
# <a name="sql_ard_type"></a>SQL_ARD_TYPE
Идентификатор типа SQL_ARD_TYPE используется для указания того, что данные в буфере будут принадлежать к типу, указанному в поле SQL_DESC_CONCISE_TYPE объекта АРД. SQL_ARD_TYPE вводится в аргумент *TargetType* вызова **SQLGetData** вместо определенного типа данных и позволяет приложению изменять тип данных буфера, изменяя поле дескриптора. Это значение связывает тип данных буфера * \*таржетвалуептр* с полем дескриптора. (SQL_ARD_TYPE не вводится в вызов **SQLBindCol** или **SQLBindParameter** , так как тип привязанного буфера уже связан с полями SQL_DESC_TYPE и SQL_DESC_CONCISE_TYPE и может быть изменен в любое время путем изменения любого из этих полей.)  
  
 Идентификатор типа SQL_ARD_TYPE можно использовать для указания значений, не заданных по умолчанию, для параметров с точностью до точности и с, а также значений точности и масштаба для SQL_C_NUMERICного типа данных. Дополнительные сведения см. в подразделе [Переопределение значений в начале и в секундах по умолчанию для типов данных интервала](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) и [Переопределение точности по умолчанию и масштаба для числовых типов данных](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md)далее в этом приложении.

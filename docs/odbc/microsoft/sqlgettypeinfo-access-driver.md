---
title: SQLGetTypeInfo (драйвер доступа) | Документы Microsoft
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
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b15ab4faf590850a79317ad5c4cd83342b2b707
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, полученных при **SQLGetTypeInfo** будет именем, наиболее часто используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска для байта, счетчик, Double, Single, Long и короткого типов данных. (LIKE возможность достигается путем преобразования значения в символ с помощью преобразования канонические функции ODBC, затем сравнение.)

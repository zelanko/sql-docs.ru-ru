---
title: SQLBindParameter (драйвер Excel) | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c29676a5085cd7ca826c708d7f441dfb11fa1dd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 При использовании драйвера Microsoft Excel при выполнении инструкции INSERT, в котором используется параметр, чтобы вставить значение NULL в столбец SQL_CHAR будет возвращено значение SQL_SUCCESS_WITH_INFO с кодом SQLSTATE 01004, «Усеченный данных».

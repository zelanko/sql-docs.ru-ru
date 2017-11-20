---
title: "SQLColumns (драйвер доступа) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6359fe8948e670a05a076537e2acf3e28b3cba1d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к файлу базы данных возвращается.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, участвующих в первичный ключ или уникальный индекс.|


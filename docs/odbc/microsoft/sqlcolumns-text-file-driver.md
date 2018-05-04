---
title: SQLColumns (драйвера текстового файла) | Документы Microsoft
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
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fd2ca7e37296719c7747cf93b4a7940e5941ad8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (драйвера текстового файла)
> [!NOTE]  
>  В этом разделе сведения текстовый файл драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу, возвращается.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, участвующих в первичный ключ или уникальный индекс.|

---
description: SQLColumns (драйвер для Access)
title: SQLColumns (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3fef37db9ae45591b173db8822d17399c257b423
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412180"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Возвращается путь к файлу базы данных.|  
|TABLE_OWNER|Значение NULL возвращается в этом столбце, так как имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, которые участвуют в первичном ключе или уникальном индексе.|

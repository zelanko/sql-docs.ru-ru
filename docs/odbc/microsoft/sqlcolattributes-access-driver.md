---
description: SQLColAttributes (драйвер для Access)
title: SQLColAttributes (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d9758bb5c473971d3ed9acea52559da0a4aac67d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412280"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE — это максимальная длина столбца, а не максимальная длина столбца, равная 2.|  
|SQL_OWNER_NAME|В этом столбце возвращается пустая строка (""), так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращается путь к файлу базы данных.|  
|SQL_COLUMN_SEARCHABLE|Столбцы LONGVARBINARY и LONGVARCHAR выводятся как SQL_UNSEARCHABLE.<br /><br /> Двоичные и символьные типы данных с фиксированной длиной и переменной длиной поддерживают поиск, даже если LONGVARBINARY и LONGVARCHAR не являются.|  
  
> [!NOTE]  
>  Приведенный выше список атрибутов, возвращаемых функцией **SQLColAttributes**, не является полным.

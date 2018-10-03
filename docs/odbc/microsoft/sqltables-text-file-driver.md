---
title: SQLTables (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1299af287d9826893fc8c1f93007967509704d30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811872"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера текстовый файл. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableOwner*|Единственным допустимым аргументом для *szTableOwner* имеет значение NULL, так как ни один из драйверов не поддерживает имена владельцев. С помощью *szTableOwner* присваивается значение NULL, возвращаются все таблицы. В столбце TABLE_OWNER возвращается значение NULL.|  
|*szTableQualifier*|В столбце TABLE_QUALIFIER **SQLTables** возвращает путь к каталогу.|  
|*SzTableType*|«TABLE» является единственным типом таблицы поддерживается.<br /><br /> Если используется драйвер для текстовых, список файлов, возвращенные **SQLTables** определяется расширения файлов в **списка расширений** поле **настройки текста ODBC** диалоговое окно.|

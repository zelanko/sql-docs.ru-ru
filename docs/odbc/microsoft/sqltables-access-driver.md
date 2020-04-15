---
title: СЗЛТаблицы (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df3a23af365efbef6a0f0da2c52568501425ecb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306095"
---
# <a name="sqltables-access-driver"></a>SQLTables (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableВладелец*|Единственным веским аргументом для *szTableOwner* является NULL, потому что ни один из драйверов не поддерживает имена владельцев. С *набором szTableOwner* null все таблицы возвращаются. NULL возвращается в TABLE_OWNER колонке.|  
|*szTableQualifier*|В TABLE_QUALIFIER столбца **S'LTables** вернет путь в файл базы данных.|  
|*SzTableType*|При использовании драйвера Microsoft Access "SYSTEM TABLE" поддерживается для *szTableType* для системных таблиц, "SYNONYM" поддерживается для прилагаемых таблиц, а "VIEW" поддерживается для запросов возврата строк.|  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](../../odbc/reference/syntax/sqltables-function.md)

---
title: S'LTables (драйвер dBASE) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLTables
- SQLTables function [ODBC], dBASE Driver
ms.assetid: 45938efb-b678-47d8-9345-644fa26ad679
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 242be06eafc7657f37f55ce266af471cbc72597f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306075"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableВладелец*|Единственным веским аргументом для *szTableOwner* является NULL, потому что ни один из драйверов не поддерживает имена владельцев. С *набором szTableOwner* null все таблицы возвращаются. NULL возвращается в TABLE_OWNER колонке.|  
|*szTableQualifier*|В TABLE_QUALIFIER колонке **S'LTables** вернет путь в каталог.|  
|*SzTableType*|Для файлов dBASE "TABLE" является единственным поддерживаемым типом таблицы.|

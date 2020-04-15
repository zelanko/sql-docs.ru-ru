---
title: S'LTables (Драйвер текстовых файлов) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 938ceba5da25d176628d5c1d9875383d977e3aec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299334"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableВладелец*|Единственным веским аргументом для *szTableOwner* является NULL, потому что ни один из драйверов не поддерживает имена владельцев. С *набором szTableOwner* null все таблицы возвращаются. NULL возвращается в TABLE_OWNER колонке.|  
|*szTableQualifier*|В TABLE_QUALIFIER колонке **S'LTables** вернет путь в каталог.|  
|*SzTableType*|"TABLE" является единственным поддерживаемым типом таблицы.<br /><br /> При использовании драйвера текста список файлов, возвращенных **S'LTables,** определяется расширением файлов в поле **списка расширений** в диалоговом окне **настройки текста ODBC.**|

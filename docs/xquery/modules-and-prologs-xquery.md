---
title: Модули и журналы (XQuery) | Документация Майкрософт
description: Узнайте, какие спецификации не поддерживаются при объявлении пространства имен в прологе XQuery.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 078cd9e29c917ce8842edd2269896debee074a91
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84881640"
---
# <a name="modules-and-prologs-xquery"></a>Модули и прологи (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [Пролог XQuery](../xquery/modules-and-prologs-xquery-prolog.md) — это серия объявлений пространств имен. При использовании объявленного пространства имен в прологе можно указать префикс для привязки пространства имен, а также применять префикс в теле запроса.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 В этой реализации не поддерживаются следующие возможности из спецификации XQuery:  
  
-   объявление модуля (`version`);  
  
-   объявление модуля (`module namespace`);  
  
-   Ксмпспацедекларатион ( `xmlspace` )  
  
-   объявление параметров сортировки по умолчанию (`declare default collation`);  
  
-   объявление базового URI (`declare base-uri`);  
  
-   объявление конструкции (`declare construction`);  
  
-   объявление упорядочения по умолчанию (`declare ordering`);  
  
-   импорт схемы (`import schema namespace`);  
  
-   импорт модуля (`import module`);  
  
-   объявление переменной в прологе (`declare variable`);  
  
-   объявление функции (`declare function`).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пролог XQuery](../xquery/modules-and-prologs-xquery-prolog.md)  
 Описание пролога XQuery.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  

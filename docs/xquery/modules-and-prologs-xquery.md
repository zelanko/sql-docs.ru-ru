---
title: Модули и Прологи (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: cc8c582f4a4e984bd203071f5ce59f986765e840
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291520"
---
# <a name="modules-and-prologs-xquery"></a>Модули и прологи (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [XQuery Prolog](../xquery/modules-and-prologs-xquery-prolog.md) — это последовательность объявлений пространств имен. При использовании объявленного пространства имен в прологе можно указать префикс для привязки пространства имен, а также применять префикс в теле запроса.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 В этой реализации не поддерживаются следующие возможности из спецификации XQuery:  
  
-   объявление модуля (`version`);  
  
-   объявление модуля (`module namespace`);  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   объявление параметров сортировки по умолчанию (`declare default collation`);  
  
-   объявление базового URI (`declare base-uri`);  
  
-   объявление конструкции (`declare construction`);  
  
-   объявление упорядочения по умолчанию (`declare ordering`);  
  
-   импорт схемы (`import schema namespace`);  
  
-   импорт модуля (`import module`);  
  
-   объявление переменной в прологе (`declare variable`);  
  
-   объявление функции (`declare function`).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Пролог XQuery](../xquery/modules-and-prologs-xquery-prolog.md)  
 Описание пролога XQuery.  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  

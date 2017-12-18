---
title: "Большие коллекции XML-схем и состояние нехватки памяти | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9027437a350d1e0ee25a822b2ac68a45da184bc1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Большие коллекции схем XML и условия исчерпания памяти
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] В ходе вызова встроенной функции XML_SCHEMA_NAMESPACE () применительно к большой коллекции схем XML или при попытке удалить большую коллекцию схем XML может возникнуть условие исчерпания памяти. Далее приводятся решения, которыми можно воспользоваться в данных ситуациях.  
  
-   При небольшой системной загрузке используйте команду DROP_XML_SCHEMA_COLLECTION. При неудачном выполнении команды переведите базу данных в однопользовательский режим с помощью инструкции ALTER DATABASE и попытайтесь выполнить DROP XML SCHEMA COLLECTION снова. Если коллекция XML-схем присутствует в базе данных **master**, **model**или **tempdb**, то для перехода в однопользовательский режим потребуется перезапуск сервера.  
  
-   При вызове XML_SCHEMA_NAMESPACE можно попытаться получить одиночное пространство имен XML-схемы, попробовать сделать вызов позже, когда снизится нагрузка в системе, или же попытаться произвести вызов в однопользовательском режиме.  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

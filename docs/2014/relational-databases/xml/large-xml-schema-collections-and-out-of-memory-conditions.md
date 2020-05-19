---
title: Большие коллекции XML-схем и состояние нехватки памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b5c82509505cb0497ffd67aa490e9b7d5f9b2a25
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702612"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Большие коллекции схем XML и условия исчерпания памяти
  В ходе вызова встроенной функции XML_SCHEMA_NAMESPACE () на большой коллекции схем XML или при попытке удалить большую коллекцию схем XML может возникнуть условие исчерпания памяти. Далее приводятся решения, которыми можно воспользоваться в данных ситуациях.  
  
-   При небольшой системной загрузке используйте команду DROP_XML_SCHEMA_COLLECTION. При неудачном выполнении команды переведите базу данных в однопользовательский режим с помощью инструкции ALTER DATABASE и попытайтесь выполнить DROP XML SCHEMA COLLECTION снова. Если коллекция XML-схем присутствует в базе данных **master**, **model**или **tempdb**, то для перехода в однопользовательский режим потребуется перезапуск сервера.  
  
-   При вызове XML_SCHEMA_NAMESPACE можно попытаться получить одиночное пространство имен XML-схемы, попробовать сделать вызов позже, когда снизится нагрузка в системе, или же попытаться произвести вызов в однопользовательском режиме.  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций схем XML на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  

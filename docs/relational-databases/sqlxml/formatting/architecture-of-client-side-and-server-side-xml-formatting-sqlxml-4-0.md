---
title: "Архитектура клиентские и серверные форматирование XML (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4efdc1f83a99cfc148f34a47e0843328891267b7
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Архитектура форматирования XML на стороне клиента и сервера (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
На следующей иллюстрации показана архитектура форматирования XML на стороне сервера.  
  
 ![Архитектура форматирования XML-кода на стороне сервера. ] (../../../relational-databases/sqlxml/formatting/media/serversidexml.gif "Форматирования архитектура XML-кода на стороне сервера.")  
  
 В этом примере команда, указанная на стороне клиента, передается на сервер. Сервер создает XML-документ и возвращает его клиенту. В этом случае сервер имеет экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы форматировать XML-документ на стороне сервера, можно применять либо поставщик SQLXMLOLEDB, либо SQLOLEDB.  Поставщик SQLXMLOLEDB использует библиотеку Sqlxml4.dll, входящую в SQLXML 4.0. Если используется поставщик SQLOLEDB, по умолчанию получаем функциональность SQLXML, предоставляемую библиотекой Sqlxmlx.dll, входящей в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, или компоненты доступа к данным MDAC 2.6 или более поздней версии. Чтобы использовать библиотеку Sqlxml4.dll с поставщиком SQLOLEDB, необходимо задать свойства версии SQLXML «SQLXML.4.0» для объекта SQLOLEDB Connection. В любом случае сервер создает XML-документ и передает его клиенту.  
  
> [!NOTE]  
>  Запросы XPath и диаграммы обновления анализируются на клиенте. Чтобы вернуть шаблон XPath или диаграмму обновления в SQLXML 4.0, используйте библиотеку Sqlxml4.dll.  
  
 На следующей иллюстрации показана архитектура форматирования XML на стороне клиента.  
  
 ![Архитектура форматирования XML-кода на стороне клиента. ] (../../../relational-databases/sqlxml/formatting/media/clientsidexml.gif "Архитектура из XML-форматирование на стороне клиента.")  
  
 В этом примере клиент использует поставщик SQLXMLOLEDB. В строке подключения поставщик данных свойство должно быть присвоено значение SQLOLEDB. Это единственное допустимое значение в SQLXML 4.0. Выполняемая на клиенте команда отправляется на сервер. Созданный на сервере набор строк отправляется клиенту. Форматирование XML-документа на основе набора строк выполняется на стороне клиента.  
  
 В SQLXML 4.0 в качестве поставщика данных может использоваться собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11) или поставщик SQLOLEDB. Теоретически можно получить доступ к любому источнику данных. Если запрос возвращает единственный набор строк, преобразование XML может применяться на клиенте.  
  
  

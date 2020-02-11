---
title: SQL Server ADO.NET расширения в процессе
description: Ссылки на статьи о четырех основных функциональных расширениях для ADO.NET, специально предназначенных для внутрипроцессного использования.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: f3c1729d216a1456551da3699c286385694e558a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258172"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Внутрипроцессные расширения SQL Server для ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Существует четыре основных функциональных расширения для ADO.NET, которые специально предназначены для внутрипроцессного использования. Эти расширения подробно рассматриваются в следующих разделах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Объект SqlContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 Этот класс предоставляет доступ к другим расширениям, абстрагируя контекст вызывающего объекта процедуры SQL Server, которая выполняет управляемый внутрипроцессный код.  
  
 [Объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 Этот класс содержит процедуры для отправки табличных результатов и сообщений клиенту.  
  
 [SqlTriggerContext, объект](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 Этот класс предоставляет сведения о контексте, в котором выполняется триггер.  
  
 [Объект SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 Класс SqlDataRecord представляет одну строку данных вместе со связанными с ней метаданными, позволяя хранимым процедурам возвращать клиенту пользовательские результирующие наборы.  
  
  

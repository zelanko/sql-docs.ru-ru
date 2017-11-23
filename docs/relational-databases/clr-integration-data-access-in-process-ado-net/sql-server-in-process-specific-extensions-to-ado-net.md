---
title: "SQL Server в процессе определенного расширения для ADO.NET | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9bb40ea8508fcd9c015fba6b8d7501b9207941f0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Внутрипроцессные расширения SQL Server для ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Существует четыре основных функциональных расширения для ADO.NET, специально предназначены для внутрипроцессного использования. Эти расширения подробно рассматриваются в следующих разделах.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Объект SqlContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 Этот класс предоставляет доступ к другим расширениям, абстрагируя контекст вызывающего объекта процедуры SQL Server, которая выполняет управляемый внутрипроцессный код.  
  
 [Объект SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 Этот класс содержит процедуры для отправки табличных результатов и сообщений клиенту.  
  
 [Объект SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 Этот класс предоставляет сведения о контексте, в котором выполняется триггер.  
  
 [Объект SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 Класс SqlDataRecord представляет одну строку данных вместе со связанными с ней метаданными, позволяя хранимым процедурам возвращать клиенту пользовательские результирующие наборы.  
  
  

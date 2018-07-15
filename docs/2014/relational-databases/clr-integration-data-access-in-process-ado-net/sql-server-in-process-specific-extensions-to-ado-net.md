---
title: Специальные расширения SQL Server в процессе для ADO.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bd625f2b09f70e7356c169248953786c70dd1ad9
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354946"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Внутрипроцессные расширения SQL Server для ADO.NET
  Существует четыре основных функциональных расширения для ADO.NET, которые специально предназначены для внутрипроцессного использования. Эти расширения подробно рассматриваются в следующих разделах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Объект SqlContext](sqlcontext-object.md)  
 Этот класс предоставляет доступ к другим расширениям, абстрагируя контекст вызывающего объекта процедуры SQL Server, которая выполняет управляемый внутрипроцессный код.  
  
 [Объект SqlPipe](sqlpipe-object.md)  
 Этот класс содержит процедуры для отправки табличных результатов и сообщений клиенту.  
  
 [Объект SqlTriggerContext](sqltriggercontext-object.md)  
 Этот класс предоставляет сведения о контексте, в котором выполняется триггер.  
  
 [Объект SqlDataRecord](sqldatarecord-object.md)  
 Класс SqlDataRecord представляет одну строку данных вместе со связанными с ней метаданными, позволяя хранимым процедурам возвращать клиенту пользовательские результирующие наборы.  
  
  

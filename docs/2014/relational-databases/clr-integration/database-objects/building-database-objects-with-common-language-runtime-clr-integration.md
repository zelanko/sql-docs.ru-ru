---
title: Построение объектов базы данных, интеграции среды выполнения (CLR) со средой | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
caps.latest.revision: 47
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 72d68e213d240e3c6182f99e8c1637c1f1ebedfb
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351016"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>Создание объектов базы данных с интеграцией со средой CLR
  Вы можете создавать объекты базы данных с помощью [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] называется «подпрограммы среды CLR». Эти подпрограммы включают:  
  
-   определяемые пользователем функции, возвращающие скалярное значение (скалярные определяемые пользователем функции);  
  
-   определяемые пользователем функции, возвращающие табличные значения (возвращающие табличное значение функции);  
  
-   определяемые пользователем процедуры (определяемые пользователем процедуры);  
  
-   определяемые пользователем триггеры.  
  
 Подпрограммы CLR в управляемом коде имеют одинаковую структуру. Они сопоставляются с публичными статическими методами класса (используемыми совместно с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET). Кроме подпрограмм, с помощью .NET Framework можно определять пользовательские типы (UDT) и определяемые пользователем агрегатные функции. Определяемые пользователем типы и определяемые пользователем статистические функции сопоставляются с целыми классами .NET Framework.  
  
 Каждый тип подпрограмма .NET Framework имеет [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] , [!INCLUDE[tsql](../../../includes/tsql-md.md)] эквивалент может использоваться. Например, скалярные определяемые пользователем функции могут использоваться во всех скалярных выражениях. Возвращающая табличное значение функция может использоваться в любом предложении FROM. Процедура может вызываться в инструкции EXEC или из клиентского приложения.  
  
> [!NOTE]  
>  Выполнение объекта CLR (определяемой пользователем функции, определяемого пользователем типа или триггера) в среде CLR может производиться в нескольких потоках (параллельный план), если оптимизатор запросов посчитает это более выгодным. Однако, если доступ к данным выполняет определяемая пользователем функция, выполнение будет осуществляться согласно последовательному плану. При выполнении на сервере, имеющем версию, предшествующую [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], в случае, если определяемая пользователем функция содержит параметры или возвращает значения больших объектов (LOB), выполнение также должно производиться согласно последовательному плану.  
  
 В следующей таблице приводится список подразделов этого раздела.  
  
 [Приступая к работе с интеграцией со средой CLR](getting-started-with-clr-integration.md)  
 Содержит краткие общие сведения о библиотеках и пространствах имен, необходимых для компиляции объектов с помощью интеграции со средой CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Включает пример хранимой процедуры CLR «Hello World».  
  
 [Поддерживаемые библиотеки платформы .NET Framework](supported-net-framework-libraries.md)  
 Содержит сведения о библиотеках .NET Framework, поддерживаемых интеграцией со средой CLR.  
  
 [Ограничения модели программирования на основе интеграции со средой CLR](clr-integration-programming-model-restrictions.md)  
 Содержит сведения об ограничениях модели программирования интеграции со средой CLR.  
  
 [Типы данных SQL Server в платформе .NET Framework](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 Общие сведения о типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и их эквивалентах в .NET Framework.  
  
 [Общие сведения о пользовательских атрибутах интеграции со средой CLR](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 Содержит сведения о пользовательских атрибутах интеграции со средой CLR.  
  
 [Определяемые пользователем функции среды CLR](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 Описывает реализацию и использование различных типов функций CLR: возвращающих табличное значение, скалярных и определяемых пользователем агрегатных функций.  
  
 [Определяемые пользователем типы в CLR](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Показывает, как реализовать и использовать определяемые пользователем типы данных CLR.  
  
 [Хранимые процедуры CLR](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 Показывает, как реализовать и использовать хранимые процедуры CLR.  
  
 [Триггеры CLR](../../../database-engine/dev-guide/clr-triggers.md)  
 Показывает, как реализовать и использовать триггеры CLR.  
  
## <a name="see-also"></a>См. также  
 [Среда CLR &#40;CLR&#41; Общие сведения об интеграции](../common-language-runtime-integration-overview.md)  
  
  

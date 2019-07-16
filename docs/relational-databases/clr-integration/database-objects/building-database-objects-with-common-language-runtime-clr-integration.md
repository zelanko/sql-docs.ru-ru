---
title: Построение объектов базы данных, интеграции среды выполнения (CLR) со средой | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 7037105391425632dba0af3646635305e510f207
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138669"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>Создание объектов базы данных с интеграцией со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объекты базы данных можно создавать с помощью интеграции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] со средой CLR платформы .NET Framework. Управляемый код, выполняющийся в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] называется «подпрограммы среды CLR». Эти подпрограммы включают:  
  
-   определяемые пользователем функции, возвращающие скалярное значение (скалярные определяемые пользователем функции);  
  
-   определяемые пользователем функции, возвращающие табличные значения (возвращающие табличное значение функции);  
  
-   определяемые пользователем процедуры (определяемые пользователем процедуры);  
  
-   определяемые пользователем триггеры.  
  
 Подпрограммы CLR в управляемом коде имеют одинаковую структуру. Они сопоставляются с публичными статическими методами класса (используемыми совместно с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET). Кроме подпрограмм, с помощью .NET Framework можно определять пользовательские типы (UDT) и определяемые пользователем агрегатные функции. Определяемые пользователем типы и определяемые пользователем статистические функции сопоставляются с целыми классами .NET Framework.  
  
 Каждый вид подпрограммы .NET Framework имеет декларацию [!INCLUDE[tsql](../../../includes/tsql-md.md)] и может использоваться в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] везде, где может использоваться его эквивалент [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Например, скалярные определяемые пользователем функции могут использоваться во всех скалярных выражениях. Возвращающая табличное значение функция может использоваться в любом предложении FROM. Процедура может вызываться в инструкции EXEC или из клиентского приложения.  
  
> [!NOTE]  
>  Выполнение объекта CLR (определяемой пользователем функции, определяемого пользователем типа или триггера) в среде CLR может производиться в нескольких потоках (параллельный план), если оптимизатор запросов посчитает это более выгодным. Однако, если доступ к данным выполняет определяемая пользователем функция, выполнение будет осуществляться согласно последовательному плану. При выполнении на сервере, имеющем версию, предшествующую [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], в случае, если определяемая пользователем функция содержит параметры или возвращает значения больших объектов (LOB), выполнение также должно производиться согласно последовательному плану.  
  
 В следующей таблице приводится список подразделов этого раздела.  
  
 [Приступая к работе с интеграцией со средой CLR](../../../relational-databases/clr-integration/database-objects/getting-started-with-clr-integration.md)  
 Содержит краткие общие сведения о библиотеках и пространствах имен, необходимых для компиляции объектов с помощью интеграции со средой CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Включает пример хранимой процедуры CLR «Hello World».  
  
 [Поддерживаемые библиотеки платформы .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)  
 Содержит сведения о библиотеках .NET Framework, поддерживаемых интеграцией со средой CLR.  
  
 [Ограничения модели программирования на основе интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
 Содержит сведения об ограничениях модели программирования интеграции со средой CLR.  
  
 [Типы данных SQL Server в платформе .NET Framework](../../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 Общие сведения о типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и их эквивалентах в .NET Framework.  
  
 [Общие сведения о пользовательских атрибутах интеграции со средой CLR](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)  
 Содержит сведения о пользовательских атрибутах интеграции со средой CLR.  
  
 [Определяемые пользователем функции среды CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 Описывает реализацию и использование различных типов функций CLR: возвращающих табличное значение, скалярных и определяемых пользователем агрегатных функций.  
  
 [Определяемые пользователем типы в CLR](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Показывает, как реализовать и использовать определяемые пользователем типы данных CLR.  
  
 [Хранимые процедуры CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)  
 Показывает, как реализовать и использовать хранимые процедуры CLR.  
  
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
 Показывает, как реализовать и использовать триггеры CLR.  
  
## <a name="see-also"></a>См. также  
 [Среда CLR &#40;CLR&#41; Общие сведения об интеграции](../../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
  
  

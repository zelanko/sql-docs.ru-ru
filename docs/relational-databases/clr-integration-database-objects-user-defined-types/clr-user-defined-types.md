---
title: Определяемые пользователем типы данных CLR | Документация Майкрософт
description: В этой статье описывается процесс создания определяемых пользователем типов (UDT) для хранения объектов среды CLR в базе данных SQL Server.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: b3983459ac8ca4b38c82cc926c2f1b0f55bb1d58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487891"
---
# <a name="clr-user-defined-types"></a>Определяемые пользователем типы данных CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]дает возможность создавать объекты базы данных, которые запрограммированы для сборки, созданной в .NET Framework среде CLR. Объекты базы данных, которые способны пользоваться преимуществами многофункциональной модели программирования, предоставляемыми средой CLR, содержат триггеры, хранимые процедуры, функции, агрегатные функции и типы.  
  
> [!NOTE]  
>  По умолчанию возможность выполнять код CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отключена. Среду CLR можно включить с помощью системной хранимой процедуры **sp_configure** .  
  
 Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], можно использовать определяемые пользователем типы для расширения системы скалярных типов сервера, что позволяет хранить объекты среды CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных. Определяемые пользователем типы могут состоять из несколько элементов, а их поведение может отличаться от обычных типов данных, обозначенных псевдонимами, каждый из которых состоит из одного системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Система обращается к определяемым пользователем типам как к единым объектам, поэтому их использование для сложных типов данных может негативно отразиться на производительности. Для моделирования сложных данных лучше подходят обычные строки и таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяемые пользователем типы хорошо подходят для представления следующих данных:  
  
-   Значения даты, времени, валюты и расширенные числовые типы  
  
-   Данные геопространственных приложений  
  
-   Закодированные или зашифрованные данные  
  
 Процесс разработки определяемых пользователем типов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит из следующих шагов.  
  
1.  **Кодирование и построение сборки, определяющей определяемый пользователем тип.** Определяемые пользователем типы определяются с помощью любого языка, поддерживаемого средой CLR платформы .NET Framework и создающего проверяемый код. Среди таких языков Visual C# и Visual Basic .NET. Доступ к данным предоставляется как к полям и свойствам класса или структуры платформы .NET Framework, а поведение определяется методами класса или структуры.  
  
2.  **Регистрирует сборку.** Развертывание определяемых пользователем типов в проекте базы данных может быть выполнено с помощью пользовательского интерфейса Visual Studio или с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY, которая копирует сборку, содержащую класс или структуру, в базу данных.  
  
3.  **Создание определяемого пользователем типа в SQL Server.** После загрузки сборки в базу данных определяемый пользователем тип создается с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], а доступ к элементам класса или структуры представляется как к элементам этого типа. Определяемые пользователем типы существуют только в контексте одной базы данных, а после регистрации они не имеют зависимостей от внешних файлов, из которых были созданы.  
  
    > [!NOTE]  
    >  До выхода версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] определяемые пользователем типы, созданные на основе сборок платформы .NET Framework, не поддерживались. Однако вы по-прежнему можете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать псевдонимы типов данных с помощью **sp_addtype**. Синтаксис CREATE TYPE можно использовать для создания собственных определяемых пользователем типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и определяемых пользователем типов.  
  
4.  **Создание таблиц, переменных или параметров с помощью определяемого пользователем типа** Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], определяемый пользователем тип может использоваться в качестве определения столбца таблицы, в виде переменной в [!INCLUDE[tsql](../../includes/tsql-md.md)] пакете или в качестве аргумента [!INCLUDE[tsql](../../includes/tsql-md.md)] функции или хранимой процедуры.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
 Описывает способ создания определяемых пользователем типов.  
  
 [Регистрация определяемых пользователем типов в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/registering-user-defined-types-in-sql-server.md)  
 Описывает, как регистрировать определяемые пользователем типы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и как управлять ими.  
  
 [Работа с определяемыми пользователем типами в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
 Описывает способ создания запросов при помощи определяемых пользователем типов.  
  
 [Доступ к определяемым пользователем типам в ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
 Описывает способ работы с определяемыми пользователем типами при помощи поставщика данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в ADO.NET.  
  
  

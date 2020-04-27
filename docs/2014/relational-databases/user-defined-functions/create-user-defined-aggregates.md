---
title: Создание определяемых пользователем агрегатных функций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23d5180928f4f3335aa17dff61b50e6fdd19549f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68196472"
---
# <a name="create-user-defined-aggregates"></a>Создание определяемых пользователем агрегатных функций
  Можно создать объект базы данных внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который запрограммирован в сборке среды CLR. В число объектов базы данных, способных эффективно использовать предоставляемую средой CLR многофункциональную модель программирования, входят триггеры, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Подобно встроенным агрегатным функциям, предоставленным в [!INCLUDE[tsql](../../includes/tsql-md.md)], пользовательские агрегатные функции производят вычисление в ряде значений и возвращают одиночное значение.  
  
 Создание пользовательской агрегатной функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает в себя следующие шаги.  
  
-   Определите пользовательскую агрегатную функцию как класс на языке, поддерживаемом платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET. Дополнительные сведения о программировании определяемых пользователем статистических функций в среде CLR см. в статье [Пользовательские агрегатные функции среды CLR](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Скомпилируйте этот класс для построения сборки среды CLR, используя соответствующий языку компилятор.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../clr-integration/assemblies-database-engine.md).  
  
-   Создайте пользовательское статистическое выражение, которое ссылается на зарегистрированную сборку, используя инструкцию CREATE AGGREGATE.  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает пользовательские статистические функции в базе данных для всех классов, которые могут иметь атрибут `SqlUserDefinedAggregate`. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Создание, изменение или удаление сборки**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Создание пользовательской статистической функции**  
  
-   [CREATE AGGREGATE (Transact-SQL)](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

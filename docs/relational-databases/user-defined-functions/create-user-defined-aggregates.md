---
title: "Создание определяемых пользователем агрегатных функций | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-udf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fcade160089ec8e066f830804dab88715ceffcaf
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-user-defined-aggregates"></a>Создание определяемых пользователем агрегатных функций
  Можно создать объект базы данных внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который запрограммирован в сборке среды CLR. В число объектов базы данных, способных эффективно использовать предоставляемую средой CLR многофункциональную модель программирования, входят триггеры, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Подобно встроенным агрегатным функциям, предоставленным в [!INCLUDE[tsql](../../includes/tsql-md.md)], пользовательские агрегатные функции производят вычисление в ряде значений и возвращают одиночное значение.  
  
 Создание пользовательской агрегатной функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает в себя следующие шаги.  
  
-   Определите пользовательскую агрегатную функцию как класс на языке, поддерживаемом платформой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET. Дополнительные сведения о программировании определяемых пользователем статистических функций в среде CLR см. в статье [Пользовательские агрегатные функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Скомпилируйте этот класс для построения сборки среды CLR, используя соответствующий языку компилятор.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Сборки (компоненты Database Engine)](../../relational-databases/clr-integration/assemblies-database-engine.md).  
  
-   Создайте пользовательское статистическое выражение, которое ссылается на зарегистрированную сборку, используя инструкцию CREATE AGGREGATE.  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает пользовательские статистические функции в базе данных для всех классов, которые могут иметь атрибут **SqlUserDefinedAggregate** . Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 **Создание, изменение или удаление сборки**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Создание пользовательской статистической функции**  
  
-   [CREATE AGGREGATE (Transact-SQL)](../../t-sql/statements/create-aggregate-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  


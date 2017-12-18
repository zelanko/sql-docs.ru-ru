---
title: "Создание триггеров CLR | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: triggers
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-dml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1563e6116b0c83fa7cb7f400f7516387a605fc28
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-clr-triggers"></a>Создание триггеров CLR
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создавать объекты базы данных, запрограммированные в составе сборки, созданной в среде CLR платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Объекты базы данных, способные эффективно использовать многофункциональную модель программирования, реализованную в среде CLR, включают триггеры DML и DDL, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Шаги создания триггера CLR (DML или DDL) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующие.  
  
-   Определите триггер как класс языка, поддерживаемого платформой .NET Framework. Дополнительные сведения о программировании триггеров CLR см. в разделе [Триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c). После этого следует скомпилировать класс, чтобы создать сборку в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , используя компилятор соответствующего языка.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../../relational-databases/clr-integration/assemblies-database-engine.md).  
  
-   Создайте триггер со ссылкой на зарегистрированную сборку.  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает триггеры CLR в базе данных для всех методов, аннотированных в атрибуте **SqlTrigger** . Дополнительные сведения см. в статье [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 **Создание, изменение или удаление сборки**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
-   [DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **Добавление триггера CRL**  
  
-   [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DML](../../relational-databases/triggers/dml-triggers.md)   
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Доступ к данным из объектов среды CLR для работы с базами данных](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  

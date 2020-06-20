---
title: Создание триггеров CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 3afd841b4f1f9ca567a93c0a20c0a7609a5b45e2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043028"
---
# <a name="create-clr-triggers"></a>Создание триггеров CLR
  Внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создавать объекты базы данных, запрограммированные в составе сборки, созданной в среде CLR платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Объекты базы данных, способные эффективно использовать многофункциональную модель программирования, реализованную в среде CLR, включают триггеры DML и DDL, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Шаги создания триггера CLR (DML или DDL) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующие.  
  
-   Определите триггер как класс языка, поддерживаемого платформой .NET Framework. Дополнительные сведения о программировании триггеров CLR см. в разделе [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md). После этого следует скомпилировать класс, чтобы создать сборку в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , используя компилятор соответствующего языка.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../clr-integration/assemblies-database-engine.md).  
  
-   Создайте триггер со ссылкой на зарегистрированную сборку.  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает триггеры CLR в базе данных для всех методов, аннотированных в атрибуте `SqlTrigger`. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Создание, изменение или удаление сборки**  
  
-   [CREATE ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Добавление триггера CRL**  
  
-   [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DML](dml-triggers.md)   
 [Основные понятия о программировании интеграции со средой (CLR)](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Доступ к данным из объектов среды CLR для работы с базами данных](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  

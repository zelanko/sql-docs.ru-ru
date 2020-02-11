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
manager: craigg
ms.openlocfilehash: b68531b962b10785927c6212b2483f2d9c1d7d3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62698831"
---
# <a name="create-clr-triggers"></a>Создание триггеров CLR
  Можно создать объект базы данных внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запрограммированный в сборке, созданной в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] среде CLR. Объекты базы данных, способные эффективно использовать многофункциональную модель программирования, реализованную в среде CLR, включают триггеры DML и DDL, хранимые процедуры, функции, агрегатные функции и типы.  
  
 Шаги создания триггера CLR (DML или DDL) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующие.  
  
-   Определите триггер как класс языка, поддерживаемого платформой .NET Framework. Дополнительные сведения о программировании триггеров CLR см. в разделе [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md). После этого следует скомпилировать класс, чтобы создать сборку в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , используя компилятор соответствующего языка.  
  
-   Зарегистрируйте сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Дополнительные сведения о работе со сборками в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Сборки (компонент Database Engine)](../clr-integration/assemblies-database-engine.md).  
  
-   Создайте триггер со ссылкой на зарегистрированную сборку.  
  
> [!NOTE]  
>  Развертывание проекта SQL Server в [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрирует сборку в базе данных, указанной для проекта. Развертывание проекта также создает триггеры CLR в базе данных для всех методов, аннотированных в атрибуте `SqlTrigger`. Дополнительные сведения см. в статье [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Возможность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять код CLR по умолчанию отключена. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пока параметр [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) не получит значение True с помощью хранимой процедуры [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Создание, изменение или удаление сборки**  
  
-   [Создание сборки &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [УДАЛИТЬ СБОРКУ &#40;&#41;Transact-SQL](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Создание триггера CLR**  
  
-   [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Триггеры DML](dml-triggers.md)   
 [Общеязыковая среда выполнения &#40;концепции программирования интеграции&#41; среды CLR](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Доступ к данным из объектов среды CLR для работы с базами данных](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  

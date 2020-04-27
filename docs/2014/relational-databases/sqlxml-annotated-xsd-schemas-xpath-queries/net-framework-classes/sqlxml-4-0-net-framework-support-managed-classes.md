---
title: Управляемые классы SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 677d769f54dab338e65b171bed50b6abb69e356a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010788"
---
# <a name="sqlxml-managed-classes"></a>управляемые классы SQLXML
  Управляемые классы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML предоставляют возможности SQLXML 4.0 в платформе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. С помощью управляемых классов SQLXML можно писать приложения на языке C# для доступа к XML-данным из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], доставлять данные в среду .NET Framework, обрабатывать их и отправлять обновления обратно в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в виде дельты для применения изменений. При применении изменений к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью управляемых классов SQLXML необходимо использовать схему сопоставления. Рабочий пример см. в разделе [доступ к функциям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Для использования управляемых классов SQLXML с SQLXML 4.0 следует установить среду Microsoft Visual Studio.  
  
> [!NOTE]  
>  Платформа .NET Framework включает поставщик данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Этот поставщик может использоваться для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из платформы .NET. Однако он может обрабатывать только стандартные запросы SQL (то есть запросы реляционных баз данных, за исключением запросов FOR XML). В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] нельзя выполнять XML-шаблоны или запросы XPath со стороны сервера.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Объектная модель управляемых классов SQLXML](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 Документирует управляемые классы SQLXML, их свойства и методы.  
  
 [Использование управляемых классов SQLXML](sqlxml-4-0-net-framework-support-managed-classes.md)  
 Содержит примеры использования управляемых классов SQLXML.  
  
  

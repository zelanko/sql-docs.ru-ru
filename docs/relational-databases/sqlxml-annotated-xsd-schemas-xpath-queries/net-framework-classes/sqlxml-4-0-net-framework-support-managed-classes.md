---
title: "Управляемые классы SQLXML | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
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
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f2d79aae0c863030a478ed2e3859785d491be61
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>SQLXML 4.0 поддержка платформы .NET Framework — управляемые классы
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 поддерживает функции, которые позволяют создавать приложения для доступа к XML-данных из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], переводят данные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] среды .NET Framework, обрабатывают данные и отправляют обновления назад в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  
  Управляемые классы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML предоставляют возможности SQLXML 4.0 в платформе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. С помощью управляемых классов SQLXML можно писать приложения на языке C# для доступа к XML-данным из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], доставлять данные в среду .NET Framework, обрабатывать их и отправлять обновления обратно в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в виде дельты для применения изменений. При применении изменений к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью управляемых классов SQLXML необходимо использовать схему сопоставления. Работающий пример см. в разделе [доступ к функциональным возможностям SQLXML в среде .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Для использования управляемых классов SQLXML с SQLXML 4.0 следует установить среду Microsoft Visual Studio.  
  
> [!NOTE]  
>  Платформа .NET Framework включает поставщик данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Этот поставщик может использоваться для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из платформы .NET. Однако он может обрабатывать только стандартные запросы SQL (то есть запросы реляционных баз данных, за исключением запросов FOR XML). В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] нельзя выполнять XML-шаблоны или запросы XPath со стороны сервера.  

 Сведения о доступе и изменении данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, а также об использовании дельт для обновления данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы, см. [доступ к функциональным возможностям SQLXML в среде .NET](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  Можно также составить приложения [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio для массовой загрузки XML-документов с использованием массовой загрузки XML. Дополнительные сведения см. в разделе [выполнении массовой загрузки XML-данных &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md). Необходимо добавить в приложение ссылку на DLL-библиотеку массовой загрузки XML (Xblkld4.dll). Это DLL-библиотека COM, для которой Visual Studio .NET автоматически создает библиотеку-упаковщик.  
  
  Этот раздел содержит образцы приложений, которые демонстрируют использование [!INCLUDE[msCoName](../../../includes/msconame-md.md)] управляемых классов SQLXML:  
 [Выполнение запросов SQL &#40; SQLXML управляемые классы &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [Выполнение запросов SQL с использованием метода ExecuteXMLReader](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [Обработка XML на стороне клиента &#40; SQLXML управляемые классы &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [Выполнение запросов XPath &#40; SQLXML управляемые классы &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [Выполнение запросов XPath с пространствами имен &#40; SQLXML управляемые классы &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [Выполнение файлов шаблонов с использованием свойства CommandText](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [Выполнение файлов шаблонов с использованием свойства CommandStream](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [Применение преобразования XSL &#40; SQLXML управляемые классы &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  

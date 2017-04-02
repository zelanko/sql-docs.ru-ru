---
title: "Работа с аспектами управления на основе политик | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "просмотр аспектов управления на основе политик"
  - "аспекты [управление на основе политик], копирование"
  - "аспекты [управление на основе политик], просмотр"
  - "копирование аспектов управления на основе политик"
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
caps.latest.revision: 29
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 29
---
# Работа с аспектами управления на основе политик
  Аспект управления на основе политик — это ряд логических свойств, которые связаны с определенной областью, представляющей интерес с точки зрения управления. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает несколько стандартных аспектов. Например, средство настройки контактной зоны, определяющее функции, отключенные по умолчанию.  
  
 При управлении несколькими похожими средами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить аспект в одном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], скопировать состояние аспекта в файл и импортировать этот файл на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве политики. При преобразовании состояния в политику она может быть применена к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объектам экземпляров, базам данных или объектам баз данных.  
  
 Этот раздел описывает способ копирования состояния аспекта в XML-файл.  
  
##  <a name="BeforeYouBegin"></a> Разрешения  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## Просмотр и копирование состояний аспекта  
 [Просмотр аспектов управления на основе политик в объекте SQL Server](../../relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Копирование состояния аспекта управления на основе политик в XML-файл](../../relational-databases/policy-based-management/copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
---
title: "Отключение предусмотренных по умолчанию файлов журнала трассировки | Microsoft Docs"
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
  - "Лучшие решения [компонент Database Engine]"
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Отключение предусмотренных по умолчанию файлов журнала трассировки
  Это правило проверяет значение хранимой процедуры sp_configure «default trace enabled», чтобы определить, включена ли трассировка по умолчанию (значение ON (1)) или отключена (значение OFF (0)). Если параметр включен, трассировка по умолчанию предоставляет [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] данные о конфигурации и изменениях DDL. В некоторых случаях эти сведения могут оказаться полезными для клиентов и службы поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] при устранении неполадок с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## Рекомендации  
 Для установки значения параметра «default trace enabled» равным 1 используется хранимая процедура sp_configure.  
  
## Дополнительные сведения см. в разделе  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
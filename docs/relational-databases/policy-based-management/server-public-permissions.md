---
title: "Разрешения роли сервера public | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Лучшие решения [компонент Database Engine]"
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Разрешения роли сервера public
  Это правило определяет, имеет ли роль сервера public разрешения на сервер. Каждое создающееся на сервере имя входа является членом роли сервера public. Если это условие выполняется, все имена входа на сервере будут иметь разрешение на сервер.  
  
## Рекомендации  
 Не предоставляйте серверной роли public разрешения на сервер.  
  
> [!IMPORTANT]  
>  После завершения программы установки роль **PUBLIC** имеет разрешение **CONNECT** на всех конечных точках, за исключением **Dedicated Admin Connection**. Это нормально, и в обычных ситуациях не нуждается в изменении. (Управление доступом осуществляется с помощью разрешения **CONNECT SQL**, которое предоставляется автоматически при создании нового имени входа.)  
  
### Дополнительные сведения  
 [Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
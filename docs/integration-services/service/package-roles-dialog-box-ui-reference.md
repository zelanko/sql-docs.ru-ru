---
title: "Диалоговое окно &#171;Роли пакета&#187; справочника по пользовательскому интерфейсу | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.dtsserver.packageroles.f1"
helpviewer_keywords: 
  - "диалоговое окно «Роли пакетов»"
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Диалоговое окно &#171;Роли пакета&#187; справочника по пользовательскому интерфейсу
  Используйте диалоговое окно **Роли пакетов** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], чтобы указать роли на уровне базы данных, которые обладают правами на считывание пакета, и роли на уровне базы данных, которые имеют права на запись пакета. Роли на уровне баз данных определяют права только для пакетов, хранящихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**.  
  
 Дополнительные сведения о ролях уровня базы данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и их разрешениях см. в разделе [Роли служб Integration Services (службы SSIS)](../../integration-services/service/integration-services-roles-ssis-service.md).  
  
 Роли, список которых приведен в диалоговом окне, являются существующими в данный момент ролями системной базы данных **msdb** . Если роли не выбраны, то применяются роли служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] по умолчанию. По умолчанию в роль чтения включаются **db_ssisadmin**, **db_ssisoperator** и пользователь, создавший пакет. Пользователь, который является членом одной из этих ролей или является создателем пакета, может перечислять, просматривать, выполнять экспорт и запускать пакеты. По умолчанию в роль записи включается роль **db_ssisadmin** и пользователь, который создал пакет. Пользователь, который является членом этой роли, может выполнять импорт, удалять и изменять пакеты.  
  
 В столбце **ownersid** таблицы **sysssispackages** указан уникальный идентификатор безопасности пользователя, создавшего пакет.  
  
## Параметры  
 **Имя пакета**  
 Укажите имя пакета.  
  
 **Роль считывания**  
 Выберите роль из списка.  
  
 **Роль записи**  
 Выберите роль из списка.  
  
## См. также  
 [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [Общие сведения о безопасности (службы Integration Services)](../../integration-services/security/security-overview-integration-services.md)  
  
  
---
title: Упаковка ролей диалоговое окно пользовательского интерфейса в справочник | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: abdbf8215b782f5db4343365a26d479542fc2dad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62767076"
---
# <a name="package-roles-dialog-box-ui-reference"></a>Диалоговое окно «Роли пакета» справочника по пользовательскому интерфейсу
  Используйте диалоговое окно **Роли пакетов** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], чтобы указать роли на уровне базы данных, которые обладают правами на считывание пакета, и роли на уровне базы данных, которые имеют права на запись пакета. Роли на уровне баз данных определяют права только для пакетов, хранящихся в базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb**.  
  
 Дополнительные сведения о ролях уровня базы данных [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и их разрешениях см. в разделе [Роли служб Integration Services (службы SSIS)](security/integration-services-roles-ssis-service.md).  
  
 Роли, список которых приведен в диалоговом окне, являются существующими в данный момент ролями системной базы данных **msdb** . Если роли не выбраны, то применяются роли служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по умолчанию. По умолчанию в роль чтения включаются **db_ssisadmin**, **db_ssisoperator**и пользователь, создавший пакет. Пользователь, который является членом одной из этих ролей или является создателем пакета, может перечислять, просматривать, выполнять экспорт и запускать пакеты. По умолчанию в роль записи включается роль **db_ssisadmin** и пользователь, который создал пакет. Пользователь, который является членом этой роли, может выполнять импорт, удалять и изменять пакеты.  
  
 В столбце **ownersid** таблицы **sysssispackages** указан уникальный идентификатор безопасности пользователя, создавшего пакет.  
  
## <a name="options"></a>Параметры  
 **Имя пакета**  
 Укажите имя пакета.  
  
 **Роль считывания**  
 Выберите роль из списка.  
  
 **Роль записи**  
 Выберите роль из списка.  
  
## <a name="see-also"></a>См. также  
 [Роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md)   
 [Общие сведения о безопасности (службы Integration Services)](security/security-overview-integration-services.md)  
  
  

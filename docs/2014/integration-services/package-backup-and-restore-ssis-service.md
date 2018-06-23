---
title: Пакет резервного копирования и восстановления (службы SSIS) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e0effe7b8c6b18967d9d783f082614b9f039066d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190261"
---
# <a name="package-backup-and-restore-ssis-service"></a>Резервное копирование и восстановление пакетов (службы SSIS)
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] пакеты могут быть сохранены в файловой системе или в базе данных msdb, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] системной базы данных. Для пакетов, сохраненных в msdb, может выполняться резервное копирование и восстановление с помощью функций резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения о резервном копировании и восстановлении базы данных msdb см. в следующих разделах:  
  
-   [Резервное копирование и восстановление баз данных SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [Резервное копирование и восстановление системных баз данных (SQL Server)](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] включает в себя **dtutil** командной строки программы (dtutil.exec), который можно использовать для управления пакетами. Дополнительные сведения см. в статье [dtutil Utility](dtutil-utility.md).  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Файлы конфигурации, содержащиеся в пакетах, сохраняются в файловой системе. Эти файлы не копируются при создании резервной копии базы данных msdb, поэтому необходимо регулярно выполнять резервное копирование файлов конфигурации в рамках плана защиты пакетов, сохраняемых в msdb. Чтобы включить конфигурации в резервную копию базы данных msdb, следует рассмотреть использование типа конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] вместо файлов конфигурации.  
  
## <a name="packages-stored-in-the-file-system"></a>Пакеты, хранимые в файловой системе  
 Резервная копия пакетов, сохраненных в файловой системе, должна быть включена в план резервного копирования для защиты файловой системы сервера. В файле конфигурации служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , по умолчанию называющемся MsDtsSrvr.ini.xml, перечисляются папки на сервере, который контролируется службой. Должно быть обеспечено резервное копирование этих папок. Кроме того, пакеты могут сохраняться в других папках на сервере, поэтому необходимо включить эти папки в план резервного копирования.  
  
  
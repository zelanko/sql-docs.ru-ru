---
title: База данных Resource | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4595fbd7be23414f55a51c2333eee7ebe4f39899
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871111"
---
# <a name="resource-database"></a>База данных Resource
  База данных Resource — это доступная только для чтения база данных, которая содержит все системные объекты, включенные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Системные объекты физически хранятся в базе данных Resource, но логически отображаются в схеме sys любой базы данных. База данных Resource не содержит пользовательских данных или метаданных.  
  
 База данных Resource облегчает и ускоряет обновление до новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]при обновлении версии требовалось удаление и создание системных объектов. Поскольку файл базы данных Resource содержит все системные объекты, обновление производится простым копированием одного файла базы данных Resource на локальный сервер.  
  
## <a name="physical-properties-of-resource"></a>Физические свойства базы данных Resource  
 Физические файлы базы данных Resource имеют имена mssqlsystemresource.mdf и mssqlsystemresource.ldf. Эти файлы расположены в папке \<*диск*>:\Program Files\Microsoft SQL Server\MSSQL\<версия>.\<*имя_экземпляра*>\MSSQL\Binn\, и их не следует перемещать. С каждым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] связан один и только один файл mssqlsystemresource.mdf, кроме того, и экземпляры не могут использовать этот файл совместно.  
  
> [!WARNING]  
>  Обновления и пакеты обновления иногда предоставляют новую базу данных ресурсов, которая устанавливается в папку BINN. Не рекомендуется изменять расположения базы данных ресурсов. К тому же такая возможность не поддерживается.  
  
## <a name="backing-up-and-restoring-the-resource-database"></a>Резервное копирование и восстановление базы данных Resource  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет создавать резервные копии базы данных Resource. Пользователь может создать резервную копию файла mssqlsystemresource.mdf или диска с этим файлом так, будто это двоичный файл (EXE), а не файл базы данных; однако восстановить такие резервные копии с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удастся. Восстановить резервную копию файла mssqlsystemresource.mdf можно будет только вручную; при этом следует соблюдать осторожность, чтобы не перезаписать текущую базу данных Resource устаревшей или потенциально небезопасной версией.  
  
> [!IMPORTANT]  
>  После восстановления резервной копии файла mssqlsystemresource.mdf необходимо применить к ней все последующие обновления.  
  
## <a name="accessing-the-resource-database"></a>Доступ к базе данных Resource  
 База данных Resource может изменяться только специалистом службы поддержки пользователей Майкрософт либо под его руководством. База данных Resource всегда имеет идентификатор 32767. Другими важными значениями, связанными с базой данных Resource, являются номер версии и время последнего обновления базы данных.  
  
 **Чтобы определить номер версии базы данных** Resource **, используйте следующую инструкцию**:  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 **Чтобы определить, когда в последний раз обновлялась база данных** Resource **, введите**:  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 **Для доступа к определениям SQL для системных объектов используется функция OBJECT_DEFINITION:**  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a>См. также  
 [Системные базы данных](system-databases.md)  
  
 [Диагностическое соединение для администраторов баз данных](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [OBJECT_DEFINITION (Transact-SQL)](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [Запуск SQL Server в однопользовательском режиме](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  

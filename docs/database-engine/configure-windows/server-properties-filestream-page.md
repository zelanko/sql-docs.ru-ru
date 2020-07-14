---
title: Свойства SQL Server (страница FILESTREAM) | Документы Майкрософт
description: Изучите параметры FILESTREAM в SQL Server. Узнайте, как включить FILESTREAM и настроить удаленный доступ клиентов и другие свойства.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.filestream.f1
helpviewer_keywords:
- FILESTREAM [SQL Server], properties page
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 81edbd9bfc913f9d339625a993f866d44e1a313b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730932"
---
# <a name="server-properties---filestream-page"></a>Свойства SQL Server (страница FILESTREAM)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Эта страница используется, чтобы включить FILESTREAM для этой установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
 **Разрешить FILESTREAM при доступе через Transact-SQL**  
 Выберите, чтобы включить FILESTREAM для доступа [!INCLUDE[tsql](../../includes/tsql-md.md)] . Необходимо выбрать этот элемент управления, прежде чем будут доступны другие параметры управления.  
  
 **Разрешить FILESTREAM при потоковом доступе файлового ввода-вывода**  
 Выберите, чтобы разрешить потоковый доступ Win32 для FILESTREAM.  
  
 **Имя общего ресурса Windows**  
 Этот элемент управления используется для ввода имени общего ресурса Windows, в котором будут храниться данные FILESTREAM.  
  
 **Разрешить удаленным клиентам потоковый доступ к данным FILESTREAM**  
 Выберите этот элемент управления, чтобы разрешить удаленным клиентам доступ к этим данным FILESTREAM на этом сервере.  
  
## <a name="see-also"></a>См. также:  
 [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

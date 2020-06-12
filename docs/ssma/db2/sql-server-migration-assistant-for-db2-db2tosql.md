---
title: Помощник по миграции SQL Server для DB2 (DB2ToSQL) | Документация Майкрософт
description: Узнайте о SSMA для DB2 и выполните пошаговые инструкции по переносу баз данных DB2 в SQL Server или базу данных SQL Azure.
ms.prod: sql
ms.custom: ''
ms.date: 10/10/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7633f631-ffad-469a-8441-8831a6a9f932
author: Jtoland
ms.author: Jtoland
manager: murato
ms.openlocfilehash: 6788a977f4f818d72baa7d8c0b7bbc1ad927da4c
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293720"
---
# <a name="sql-server-migration-assistant-for-db2-db2tosql"></a>Помощник по миграции SQL Server для DB2 (DB2ToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для DB2 — это инструмент для переноса баз данных DB2 в [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012, [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014, [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 в Windows и Linux, [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2019 в Windows и Linux или база данных SQL Azure. SSMA для DB2 преобразует объекты базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты базы данных, создает эти объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем переносит данные из DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или.  
  
В этой документации описывается SSMA для DB2 и приводятся пошаговые инструкции по переносу баз данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В следующей таблице приведены статьи, которые помогут вам получить дополнительные сведения:  
  
## <a name="contents"></a>Содержимое  
  
|Section|Описание|  
|-----------|---------------|
|[Новые возможности в SSMA для DB2](https://msdn.microsoft.com/1cc38f85-3caa-42d0-8c76-a380c1d15c67)|Новые возможности в этой версии SSMA для DB2|  
|[Установка SSMA для клиента DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)|Содержит статьи, содержащие необходимые условия и инструкции по установке клиента SSMA для DB2 и необходимых компонентов на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Начало работы с SSMA для DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)|Представляет пользовательский интерфейс, проекты и параметры конфигурации.|  
|[Перенос баз данных DB2 в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)|Содержит общие сведения о процессе преобразования и подробные сведения о каждом шаге процесса.|  
|[Справочник по пользовательскому интерфейсу &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)|Содержит документацию для диалоговых окон SSMA для DB2.|  
|[Работа с SSMA для консоли DB2](https://msdn.microsoft.com/29d8787c-632e-4ff7-9ccc-3f7ad40480ec)|Содержит документацию по консольному приложению SSMA|  
|[Получение помощи по SSMA для DB2](https://go.microsoft.com/fwlink/?LinkID=708538&clcid=0x409)|Содержит сведения о получении дополнительной помощи.|  

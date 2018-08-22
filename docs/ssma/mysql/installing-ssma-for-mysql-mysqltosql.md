---
title: Установка SSMA для MySQL (MySqlToSql) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Installing SSMA 2008, Upgrading
ms.assetid: e89b45bd-59c1-4d23-8bd7-3dafc1947448
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 42555d5f10fc9b7b6a1b4f35164cd64f91939981
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394706"
---
# <a name="installing-ssma-for-mysql-mysqltosql"></a>Установка SSMA для MySQL (MySqlToSql)
SQL Server Migration Assistant (SSMA) для MySQL состоит из клиентского приложения, используемого для выполнения перехода с MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование функций системы MySQL перенесенных баз данных.  
  
Установите клиентское приложение на компьютере, с помощью которого будет выполнять действия по миграции. Необходимо установить расширения файлы пакета на компьютере, где будет размещаться базы данных после миграции.  Этот компьютер должен работать под управлением SQL Server.  
  
## <a name="upgrading-ssma-for-mysql"></a>Обновление SSMA для MySQL  
Если требуется выполнить обновление до более поздней версии SSMA для MySQL, необходимо сначала удалить клиент и пакет расширения server, а затем установить новую версию.  
  
## <a name="contents"></a>Содержание  
  
|||  
|-|-|  
|**Раздел**|**Описание**|  
|[Установка SSMA для MySQL клиента &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)|Предоставляет сведения и инструкции по установке клиента SSMA.|  
|[Установка компонентов SSMA в SQL Server (MySQL to SQL)](http://msdn.microsoft.com/6772d0c5-258f-4d7b-afb0-b5f810e71af1)|Содержит сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Удаление MySQL компонентов SSMA для &#40;MySQLToSql&#41;](../../ssma/mysql/removing-the-ssma-for-mysql-components-mysqltosql.md)|Предоставляет инструкции по удалению клиентской программы.|  
  
## <a name="see-also"></a>См. также  
[Миграция MySQL базы данных в SQL Server — база данных Azure SQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

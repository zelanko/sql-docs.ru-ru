---
title: "Установка SSMA для MySQL (MySqlToSql) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Installing SSMA 2008, Upgrading
ms.assetid: e89b45bd-59c1-4d23-8bd7-3dafc1947448
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77dfcacd3c84e4c6ed8409dfc2533be6a38a31ab
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-for-mysql-mysqltosql"></a>Установка SSMA для MySQL (MySqlToSql)
SQL Server Migration Assistant (SSMA) для MySQL состоит из клиентского приложения, который позволяет выполнить миграцию с MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование системных функций MySQL перенесенных баз данных.  
  
Установите клиентское приложение на компьютере, в котором будет выполнять действия по миграции. Необходимо установить пакет файлы расширений на компьютере, где будет размещаться базы данных после миграции.  Компьютер должен работать под управлением SQL Server.  
  
## <a name="upgrading-ssma-for-mysql"></a>Обновление SSMA для MySQL  
Если требуется выполнить обновление до более поздней версии SSMA для MySQL, необходимо сначала удалить клиента и пакет расширения сервера, а затем установить новую версию.  
  
## <a name="contents"></a>Содержание  
  
|||  
|-|-|  
|**Раздел**|**Description**|  
|[Установка SSMA для клиента MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)|Предоставляет сведения и инструкции по установке клиента SSMA.|  
|[Установка компонентов SSMA на SQL Server (MySQL to SQL)](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)|Сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Удаление SSMA для компонентов MySQL &#40; MySQLToSql &#41;](../../ssma/mysql/removing-the-ssma-for-mysql-components-mysqltosql.md)|Содержит инструкции по удалению клиентская программа.|  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных MySQL в SQL Server — база данных Azure SQL &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  


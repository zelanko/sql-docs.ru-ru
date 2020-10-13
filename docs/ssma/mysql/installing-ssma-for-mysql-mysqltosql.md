---
title: Установка SSMA для MySQL (MySqlToSql) | Документация Майкрософт
description: Используйте эти статьи для установки, обновления и удаления Помощник по миграции SQL Server (SSMA) для MySQL, который включает клиентское приложение и пакет расширений.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing SSMA 2008, Upgrading
ms.assetid: e89b45bd-59c1-4d23-8bd7-3dafc1947448
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 9371043395b11258b95f20af59fd8b260f32c942
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987870"
---
# <a name="installing-ssma-for-mysql-mysqltosql"></a>Установка SSMA для MySQL (MySqlToSql)
Помощник по миграции SQL Server (SSMA) для MySQL состоит из клиентского приложения, которое используется для выполнения миграции с MySQL на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Он также содержит пакет расширений, который поддерживает перенос данных и использование системных функций MySQL в перенесенных базах данных.  
  
Установите клиентское приложение на компьютере, с которого будут выполняться действия по переносу. Необходимо установить файлы пакета расширения на компьютере, где будут размещаться перенесенные базы данных.  На этом компьютере должен быть установлен SQL Server.  
  
## <a name="upgrading-ssma-for-mysql"></a>Обновление SSMA для MySQL  
Если вы хотите выполнить обновление до более поздней версии SSMA для MySQL, сначала необходимо удалить клиент и пакет расширений сервера, а затем установить более новую версию.  
  
## <a name="contents"></a>Содержимое  
  
|Раздел|Описание|  
|-|-|  
|[Установка SSMA для клиента MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)|Содержит сведения и инструкции по установке клиента SSMA.|  
|[Установка компонентов SSMA на SQL Server (MySQL в SQL)](./installing-ssma-components-on-sql-server-mysqltosql.md)|Содержит сведения и инструкции по установке пакета расширения на экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Удаление SSMA для компонентов MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/removing-the-ssma-for-mysql-components-mysqltosql.md)|Содержит инструкции по удалению клиентской программы.|  
  
## <a name="see-also"></a>См. также:  
[Перенос баз данных MySQL в SQL Server базы данных SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  

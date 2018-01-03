---
title: "Установка SSMA для MySQL клиента (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 20e2b46e1b020865359431a4999e097c20e14da1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Установка SSMA для MySQL клиента (MySQLToSQL)
SSMA для MySQL клиента состоит из файлов программы, которые выполняют следующие задачи:  
  
-   Подключиться к базе данных MySQL.  
  
-   Подключитесь к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
-   Преобразование объектов базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объектов SQL Azure.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
-   Переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
Этот раздел содержит необходимые условия для установки и инструкции по установке SSMA для клиента MySQL.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA для MySQL предназначен для работы с MySQL 4.1 или более поздних версиях, а также всех выпусков SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016 и базе данных SQL Azure.  
  
Прежде чем устанавливать SSMA, убедитесь в том, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздних версиях.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 доступен на носителе продукта SQL Server. Его можно также получить из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   MySQL 5.1 драйвер ODBC и подключения к базам данных MySQL, которые требуется перенести. Можно установить MySQL MySQL веб-сайта. Сведения о подключении см. в разделе [подключение к MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр SQL Server, где можно будет миграция объектов базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   В случае проектов SQL Azure доступ к и достаточные разрешения для экземпляра базы данных SQL Azure, где миграция вы объектов базы данных. Дополнительные сведения см. в разделе [подключение к базе данных SQL Azure &#40; MySQLToSQL &#41; ](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-ssma-for-mysql-client"></a>Установка SSMA для клиента MySQL  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmaformysql).  
  
После загрузки последней версии, прежде чем устанавливать SSMA нужно извлечь файлы установки.  
  
**Чтобы установить клиент SSMA**  
  
1.  Дважды щелкните SSMA для MySQL  *n* . Install.exe, где  *n*  — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, будет выведено сообщение о том, необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты перед повторным запуском программы установки.  
  
3.  Прочитайте лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для MySQL перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для MySQL.  
  
На 64-разрядном компьютере Windows продукт установлен в C:\Microsoft SQL Server Migration Assistant для MySQL.  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных MySQL в SQL Server — база данных Azure SQL &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

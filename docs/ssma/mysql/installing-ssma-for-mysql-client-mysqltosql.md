---
title: Установка SSMA для клиента MySQL (MySQLToSQL) | Документация Майкрософт
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
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: de32849e59f0244baa62a5e7784b3ec2f26aacac
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40396157"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Установка клиента SSMA для MySQL (MySQLToSQL)
SSMA для MySQL клиента состоит из программных файлов, которые выполняют следующие задачи:  
  
-   Подключитесь к базе данных MySQL.  
  
-   Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
-   Преобразование объектов базы данных MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объектов SQL Azure.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
-   Перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
Здесь приведены предварительные требования для установки и инструкции по установке SSMA для MySQL клиента.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA для MySQL предназначен для работы с MySQL 4.1 или более поздних версиях, а также всех выпусков SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016, SQL Server 2017 и базе данных SQL Azure.  
  
Перед установкой SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздних версиях или Windows Server 2008 или более поздних версий.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 доступен на носителе продукта SQL Server. Можно также получить его из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   MySQL 5.1 драйвер ODBC и подключения к базам данных MySQL, которые требуется перенести. MySQL можно установить с сайта MySQL. Сведения о подключениях см. в разделе [подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Доступ к и необходимыми разрешениями на компьютере, на котором размещается целевой экземпляр SQL Server, где вам необходимо перенести объекты базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   В случае проектов SQL Azure доступ к и необходимыми разрешениями для экземпляра базы данных SQL Azure, где вы будет миграцию объектов базы данных. Дополнительные сведения см. в разделе [подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-ssma-for-mysql-client"></a>Установка SSMA для MySQL клиента  
SSMA можно загрузить из Интернета. Чтобы загрузить последнюю версию, см. в разделе [SQL Server Migration Assistant страницу загрузки](http://aka.ms/ssmaformysql).  
  
После загрузки последней версии, необходимо извлечь файлы установки перед установкой SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для MySQL *n*. Install.exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, в том, что необходимо сначала установить необходимые компоненты. Убедитесь, что вы установили все необходимые компоненты перед повторным запуском программы установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для MySQL перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для MySQL.  
  
На 64-разрядном компьютере Windows продукт установлен в C:\Microsoft SQL Server Migration Assistant для MySQL.  
  
## <a name="see-also"></a>См. также  
[Миграция MySQL базы данных в SQL Server — база данных Azure SQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

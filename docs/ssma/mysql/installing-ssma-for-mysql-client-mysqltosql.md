---
title: Установка SSMA для клиента MySQL (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9dcdeaff1c4782453a9fd57cc709e17ad3200d28
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68086818"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Установка клиента SSMA для MySQL (MySQLToSQL)
Клиент SSMA для MySQL состоит из программных файлов, которые выполняют следующие задачи:  
  
-   Подключитесь к базе данных MySQL.  
  
-   Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
-   Преобразуйте объекты базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты или SQL Azure.  
  
-   Загрузите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
-   Перенос данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
В этом разделе приведены необходимые условия для установки и инструкции по установке SSMA для клиента MySQL.  
  
## <a name="prerequisites"></a>Предварительные требования  
SSMA для MySQL предназначен для работы с MySQL 4,1 или более поздними версиями и всеми выпусками SQL Server 2005, SQL Server 2008, SQL Server 2012, SQL Server 2014, SQL Server 2016, SQL Server 2017 и базы данных SQL Azure.  
  
Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Версия 4,0 или более поздняя [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] . [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4,0 доступна на SQL Serverном носителе. Его также можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Драйвер MySQL ODBC 5,1 и подключение к базам данных MySQL, которые необходимо перенести. MySQL можно установить с веб-сайта MySQL. Дополнительные сведения о подключении см. [в статье подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Доступ к и достаточным разрешениям на компьютере, на котором размещен целевой экземпляр SQL Server, куда будут перенесены объекты и данные базы данных. Дополнительные сведения см. [в разделе Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   В случае SQL Azureных проектов можно получить доступ к экземпляру базы данных SQL Azure и обладать достаточными разрешениями для миграции объектов и данных. Дополнительные сведения см. [в статье подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   рекомендуется 4 ГБ ОЗУ.  
  
## <a name="installing-ssma-for-mysql-client"></a>Установка клиента SSMA для MySQL  
SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmaformysql).  
  
После загрузки последней версии необходимо извлечь файлы установки, прежде чем можно будет установить SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для MySQL *n*. Install. exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если необходимые компоненты не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Перед повторным запуском программы установки убедитесь, что установлены все необходимые компоненты.  
  
3.  Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки выберите вариант **Обычная**.  
  
5.  Щелкните **Install**(Установить).  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для MySQL перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft Помощник по миграции SQL Server для MySQL.  
  
На 64-разрядном компьютере Windows продукт устанавливается в К:\микрософт Помощник по миграции SQL Server для MySQL.  
  
## <a name="see-also"></a>См. также:  
[Перенос баз данных MySQL в SQL Server Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

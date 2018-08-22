---
title: Установка SSMA для DB2 клиента (DB2ToSQL) | Документация Майкрософт
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
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c0c356d54dd74ae75962d9893968ff302e7e5f98
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395144"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Установка SSMA для DB2 клиента (DB2ToSQL)
SSMA клиента состоит из программных файлов, которые выполняют следующие задачи:  
  
-   Подключение к базе данных DB2.  
  
-   Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Преобразование объектов базы данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Здесь приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с помощью DB2 для z/OS версии 9.0 и 10.0 или DB2 для LUW версии 9.8 и 10.1 или более поздней версии и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
Перед установкой SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздних версиях или Windows Server 2008 или более поздних версий.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установочного носителя. Можно также получить его из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Поставщик Microsoft OLE DB для DB2 версии 5 или более поздней версии и подключение к базам данных DB2, которые требуется перенести.  
  
-   Доступ к и необходимыми разрешениями на компьютере, на котором размещена на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure, где вам необходимо перенести объекты базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Поставщик данных OLE DB для DB2 (Майкрософт)  
Чтобы загрузить поставщик OLE DB для DB2 версии 5.0, перейдите к [пакет дополнительных компонентов Microsoft® SQL Server® 2014](http://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA можно загрузить из Интернета. Чтобы загрузить последнюю версию, см. в разделе [SQL Server Migration Assistant страницу загрузки](http://aka.ms/ssmafordb2).  
  
После загрузки последней версии, необходимо извлечь установочные файлы от перед установкой SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для DB2 *n*. Install.exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, что сначала необходимо установить необходимые компоненты. Убедитесь, что вы установили все необходимые компоненты и затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для DB2 перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для DB2.  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Миграция DB2 баз данных в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

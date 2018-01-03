---
title: "Установка SSMA для DB2 клиента (DB2ToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
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
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cddb418e373c5ac61d2788f7e8a41d51c5976b6b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Установка SSMA для DB2 клиента (DB2ToSQL)
SSMA клиента состоит из файлов программы, которые выполняют следующие задачи:  
  
-   Подключиться к базе данных DB2.  
  
-   Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Преобразование объектов базы данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксиса.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Этот раздел содержит необходимые условия для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с DB2 для z/OS версии 9.0 и 10.0 или DB2 для LUW версии 9.8 и 10,1 или более поздней версии и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 г.  
  
Прежде чем устанавливать SSMA, убедитесь в том, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздних версиях.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] установочного носителя. Его можно также получить из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Поставщик OLEDB Microsoft для DB2 версии 5 или более поздней версии и подключения к базам данных DB2, которые требуется перенести.  
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, где можно будет миграция объектов базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40; DB2eToSQL &#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Поставщик данных OLE DB для DB2 (Майкрософт)  
Чтобы загрузить поставщик OLE DB для DB2 версии 5.0, перейдите к [пакет дополнительных компонентов Microsoft® SQL Server® 2014](http://www.microsoft.com/download/details.aspx?id=42295).  
  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmafordb2).  
  
После загрузки последней версии, нужно извлечь файлы установки из перед установкой SSMA.  
  
**Чтобы установить клиент SSMA**  
  
1.  Дважды щелкните SSMA для DB2  *n* . Install.exe, где  *n*  — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, необходимо сначала установить необходимые компоненты. Убедитесь, что устанавливать все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочитайте лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для DB2 перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для DB2.  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Миграция баз данных DB2 в SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

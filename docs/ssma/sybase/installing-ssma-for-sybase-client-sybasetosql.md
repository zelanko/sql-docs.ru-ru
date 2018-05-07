---
title: Установка SSMA для Sybase клиента (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6084947ec356b2f86404ea72de20df6514b7c8cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Установка SSMA для Sybase клиента (SybaseToSQL)
Клиент SSMA состоит из программных файлов, которые используются для подключения к серверу базы данных Sybase адаптивной Server Enterprise (ASE) и экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных SQL Azure, преобразовать ASE объекты базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или загрузить объекты в синтаксисе базу данных SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, а затем перенесите данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или Azure SQLDB.  
  
Этот раздел содержит необходимые условия для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с ASE 11.9.2 или более поздних версиях, а также всех выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Прежде чем устанавливать SSMA, убедитесь в том, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздних версиях.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4.0 или более поздней версии. Платформа .NET Framework версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] установочного носителя. Его можно также получить из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Sybase OLEDB/ADO.Net/ODBC поставщика и подключение к серверу базы данных Sybase ASE, содержащий базы данных, которые требуется перенести. Могут быть установлены с компакт-диска продукта Sybase ASE. Сведения о подключении см. в разделе [подключение к Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, где можно будет миграция объектов базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)/[подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Установка SSMA для Sybase клиента  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmaforsybase).  
  
После загрузки последней версии, нужно извлечь файлы установки из перед установкой SSMA.  
  
**Чтобы установить клиент SSMA**  
  
1.  Дважды щелкните SSMA для СУБД Sybase *n*. Install.exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, необходимо сначала установить необходимые компоненты. Убедитесь, что устанавливать все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочитайте лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для СУБД Sybase перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Sybase.  
  
Помимо SSMA программные файлы, необходимо также установить SSMA для пакета расширения Sybase на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Дополнительные сведения см. в разделе [Установка SSMA компонентов на сервере SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server — Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

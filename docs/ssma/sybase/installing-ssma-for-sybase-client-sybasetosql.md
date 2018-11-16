---
title: Установка SSMA для Sybase клиента (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6cca10f2a54a70e91e46bb8b98e9799885b5f175
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671724"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Установка клиента SSMA для Sybase (SybaseToSQL)
SSMA клиента состоит из программных файлов, которые используются для подключения к серверу базы данных Sybase Adaptive Server Enterprise (ASE) и экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, преобразовать объекты базы данных ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или синтаксис базы данных SQL Azure, загрузка объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, а затем перенести данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
Здесь приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с ASE 11.9.2 или более поздних версий и всех версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Перед установкой SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздних версиях или Windows Server 2008 или более поздних версий.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4.0 или более поздней версии. В .NET Framework версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установочного носителя. Можно также получить его из [Центр разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Поставщик Sybase OLEDB/ADO.Net/ODBC и подключение к серверу базы данных Sybase ASE с базами данных, которые требуется перенести. Поставщики можно установить с носителя продукта Sybase ASE. Сведения о подключениях см. в разделе [подключение к Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Доступ к и необходимыми разрешениями на компьютере, на котором размещена на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure, где вам необходимо перенести объекты базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)/[подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Установка SSMA для Sybase клиента  
SSMA можно загрузить из Интернета. Чтобы загрузить последнюю версию, см. в разделе [SQL Server Migration Assistant страницу загрузки](https://aka.ms/ssmaforsybase).  
  
После загрузки последней версии, необходимо извлечь установочные файлы от перед установкой SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для Sybase *n*. Install.exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, что сначала необходимо установить необходимые компоненты. Убедитесь, что вы установили все необходимые компоненты и затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Sybase перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Sybase.  
  
В дополнение к файлам программы SSMA, необходимо также установить SSMA для Sybase Extension Pack на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Установка компонентов SSMA в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

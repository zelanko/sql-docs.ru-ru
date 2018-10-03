---
title: Установка SQL Server Migration Assistant для Access (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f8dd4dcfc08366e78f11fc8b10fa269f17bb09e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708442"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Установка SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для доступа устанавливается с помощью мастера на основе установщика Windows. Этот раздел содержит сведения о необходимых компонентах установки, ссылку на последнюю версию SSMA и инструкции по установке, лицензирование, удаление и обновление SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
Перед установкой SSMA, убедитесь, что ваша система отвечает следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4.0 или более поздней версии. В .NET Framework версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диск с продуктом и, используя сведения из [руководство по Microsoft .NET](https://docs.microsoft.com/dotnet/framework/).
  
-   Доступ к и необходимыми разрешениями на компьютере, на котором размещена на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]базы данных SQL Azure, на который будет миграция объектов базы данных и данных.  
  
-   Майкрософт доступа к данным объекта (DAO) версия поставщика, 12.0 и 14.0. Установить поставщик DAO с продукта Microsoft Office 2010 или 2007 также можно загрузить с веб-сайте Майкрософт.  
  
-   SQL Server Native доступа Client (SNAC) версии 10.5 и более поздних версий для миграции в SQL Azure. Можно получить последнюю версию SNAC из [пакет дополнительных компонентов Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 ГБ ОЗУ (рекомендуется).  
  
## <a name="installing-ssma"></a>Установка SSMA  
SSMA можно загрузить из Интернета. Чтобы загрузить последнюю версию, см. в разделе [SQL Server Migration Assistant страницу загрузки](http://aka.ms/ssmaforaccess).  
  
После загрузки последней версии, необходимо извлечь установочные файлы от перед установкой SSMA.

> [!IMPORTANT]  
> -   Удалите все предыдущие версии SSMA для Access перед установкой новой версии.  
  
**Установка SSMA**  
  
1.  Дважды щелкните SSMA для Access *n*MSI-файл, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, что сначала необходимо установить необходимые компоненты. Убедитесь, что вы установили все необходимые компоненты и затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя; Если вы согласны, установите **я принимаю соглашение**, а затем нажмите кнопку **Далее**.  
  
4.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Access.  
  
## <a name="uninstalling-ssma-for-access"></a>Удаление SSMA для Access  
Удаление с помощью SSMA **Установка и удаление программ** панели управления. Имейте в виду, что при удалении программы не удаляйте файлы проекта SSMA и файлы журнала.  
  
**Чтобы удалить SSMA**  
  
1.  Нажмите кнопку **запустить**, нажмите кнопку **панели управления**, а затем нажмите кнопку **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Access**, а затем нажмите кнопку **удалить**.  
  
## <a name="upgrading-to-a-later-version"></a>Обновление до более поздней версии  
Если требуется выполнить обновление до более поздней версии SSMA для Access, необходимо сначала удалить SSMA для Access и затем установить новую версию. Следуйте инструкциям в SSMA при удалении раздела доступ для завершения этого процесса.  
  
Если открыть проект, созданный в более ранней версии SSMA для Access, SSMA запрашивает, следует ли преобразовать проект до новой версии. Нажмите кнопку **Да** для работы с проектом в более новую версию SSMA.  
  
## <a name="see-also"></a>См. также  
[Подготовка к миграции базы данных Access](preparing-access-databases-for-migration-accesstosql.md)  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Связь приложений Access SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  

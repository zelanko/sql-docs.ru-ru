---
title: "Установка SQL Server Migration Assistant для Access (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: "31"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ade7040ed4736ea0ee451154c3eed19582adcce8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Установка SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для доступа устанавливается с помощью мастера на основе установщика Windows. Этот раздел содержит сведения о необходимых компонентах установки, ссылку на последнюю версию SSMA и инструкции по установке, лицензировании, удаление и обновление SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
Прежде чем устанавливать SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4.0 или более поздней версии. Платформа .NET Framework версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] диск с продуктом и с помощью сведений в [руководство по Microsoft .NET](https://docs.microsoft.com/en-us/dotnet/framework/).
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]базу данных SQL Azure, на который будет миграция объектов базы данных и данных.  
  
-   Microsoft доступа к данным объекта (DAO) версии поставщика 12.0 и 14.0. Можно установить поставщик DAO из продукта Microsoft Office 2010 или 2007 или загрузить с веб-сайта Майкрософт.  
  
-   SQL Server Native доступа Client (SNAC) версии 10.5 и более поздних версий для миграции в SQL Azure. Можно получить последнюю версию SNAC из [пакет дополнительных компонентов Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 ГБ ОЗУ (рекомендуется).  
  
## <a name="installing-ssma"></a>Установка SSMA  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmaforaccess).  
  
После загрузки последней версии, нужно извлечь файлы установки из перед установкой SSMA.

> [!IMPORTANT]  
> -   Удалите все предыдущие версии SSMA для Access перед установкой новой версии.  
  
**Чтобы установить SSMA**  
  
1.  Дважды щелкните SSMA для Access  *n* MSI-файл, где  *n*  — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появляется сообщение, указывающее, необходимо сначала установить необходимые компоненты. Убедитесь, что устанавливать все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя; Если вы согласны, установите **я принимаю условия соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Access.  
  
## <a name="uninstalling-ssma-for-access"></a>Удаление SSMA для Access  
Удаление SSMA с помощью **Установка и удаление программ** панели управления. Имейте в виду, что удаления программы не удаляйте файлы проекта SSMA и файлы журнала.  
  
**Чтобы удалить SSMA**  
  
1.  Нажмите кнопку **запустить**, нажмите кнопку **панели управления**, а затем нажмите кнопку **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Access**, а затем нажмите кнопку **удалить**.  
  
## <a name="upgrading-to-a-later-version"></a>Обновление до более поздней версии  
Если требуется выполнить обновление до более поздней версии SSMA для Access, необходимо сначала удалить SSMA для Access и затем установить новую версию. Следуйте инструкциям в SSMA удаление раздела доступа для завершения этого процесса.  
  
Если открыть проект, созданный в более ранней версии SSMA для Access SSMA запросом для преобразования проекта до новой версии. Нажмите кнопку **Да** для работы с проектом в новой версии SSMA.  
  
## <a name="see-also"></a>См. также:  
[Подготовка к миграции базы данных Access](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Связывание приложения Access в SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  

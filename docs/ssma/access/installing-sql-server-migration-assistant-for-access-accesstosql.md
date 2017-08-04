---
title: "Установка SQL Server Migration Assistant для Access (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
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
caps.latest.revision: 31
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2915318b5bbe85ad21a5e5095a7322013dfa7b44
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Установка SQL Server Migration Assistant для Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для доступа устанавливается с помощью мастера на основе установщика Windows. Этот раздел содержит сведения о необходимые условия для установки, ссылку на последнюю версию SSMA и инструкции по установке, лицензировании, удаление и обновление SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
Прежде чем устанавливать SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4.0 или более поздней версии. Платформа .NET Framework версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] диск с продуктом и из [Центр разработчиков Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882) веб-сайта.  
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]базу данных SQL Azure, где можно будет миграция объектов базы данных и данных.  
  
-   DAO поставщика версии 12.0 и 14.0. Можно установить поставщик DAO из продукта Microsoft Office 2010 или 2007 или загрузить с веб-сайта Майкрософт.  
  
-   SQL Server Native доступа Client (SNAC) версии 10.5 и более поздних версий для миграции в SQL Azure. Можно получить последнюю версию SNAC из [пакет дополнительных компонентов Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-ssma"></a>Установка SSMA  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmaforaccess).  
  
После загрузки последней версии, нужно извлечь файлы установки из перед установкой SSMA.  
  
**Чтобы установить SSMA**  
  
1.  Дважды щелкните SSMA для Access  *n* . Install.exe, где  *n*  — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, необходимо сначала установить необходимые компоненты. Убедитесь, что устанавливать все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочитайте лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Access перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Access.  
  
## <a name="uninstalling-ssma-for-access"></a>Удаление SSMA для Access  
Удаление SSMA с помощью **Установка и удаление программ** панели управления. Имейте в виду, что удаления программы не удаляйте файлы проекта SSMA, и файлы журнала.  
  
**Чтобы удалить SSMA**  
  
1.  Нажмите кнопку **запустить**, нажмите кнопку **панели управления**, а затем нажмите кнопку **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Access**, а затем нажмите кнопку **удалить**.  
  
## <a name="upgrading-to-a-later-version"></a>Обновление до более поздней версии  
Если требуется выполнить обновление до более поздней версии SSMA для Access, необходимо сначала удалить SSMA для Access и затем установить новую версию. Следуйте инструкциям по ранее в этом разделе для удаления и установки.  
  
При открытии проекта из более ранней версии SSMA для Access SSMA запрашивает, если для преобразования проекта до новой версии. Необходимо нажать кнопку **Да** для работы с проектом в новой версии SSMA.  
  
## <a name="see-also"></a>См. также:  
[Подготовка к миграции базы данных Access](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Связывание приложения Access в SQL Server](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)  
  


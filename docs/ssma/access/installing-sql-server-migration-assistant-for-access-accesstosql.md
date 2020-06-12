---
title: Установка Помощник по миграции SQL Server для Access (Акцесстоскл) | Документация Майкрософт
description: Дополнительные сведения о предварительных требованиях для установки Помощник по миграции SQL Server (SSMA) для Access и установке, лицензировании, обновлении и удалении.
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
ms.openlocfilehash: 5ca42e406bb7483617afe6364027014650e838f2
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293761"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Установка Помощник по миграции SQL Server для Access (Акцесстоскл)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для доступа устанавливается с помощью мастера на основе установщик Windows. В этом разделе содержатся сведения о предварительных требованиях для установки, ссылка на последнюю версию SSMA и инструкции по установке, лицензированию, удалению и обновлению SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
Перед установкой SSMA убедитесь, что система соответствует следующим требованиям.  
  
-   Windows 7 или более поздней версии, или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)].NET Framework версии 4,0 или более поздней версии. Версия .NET Framework 4,0 доступна на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диске продукта и с помощью сведений в разделе [руководства по Microsoft .NET](https://docs.microsoft.com/dotnet/framework/).
  
-   Доступ к и достаточным разрешениям на компьютере, на котором размещен целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure DB, в который будут перенесены объекты и данные базы данных.  
  
-   Поставщик объектов Microsoft Data Access (DAO) версии 12,0 или 14,0. Поставщик DAO можно установить из продукта Microsoft Office 2010/2007 или загрузить с веб-сайта корпорации Майкрософт.  
  
-   SQL Server собственный клиент Access (SNAC) версии 10,5 и выше для миграции на SQL Azure. Последнюю версию SNAC можно получить с помощью [пакета дополнительных компонентов Microsoft® SQL Server® 2008 R2](https://www.microsoft.com/download/details.aspx?id=44272)  
  
-   4 ГБ ОЗУ (рекомендуется).  
  
## <a name="installing-ssma"></a>Установка SSMA  
SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmaforaccess).  
  
После загрузки последней версии необходимо извлечь файлы установки из, прежде чем можно будет установить SSMA.

> [!IMPORTANT]  
> -   Удалите все предыдущие версии SSMA для доступа перед установкой новой версии.  
  
**Установка SSMA**  
  
1.  Дважды щелкните SSMA для Access *n*. msi, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если необходимые компоненты не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки выберите вариант **Обычная**.  
  
5.  Нажмите кнопку **Установить**.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft Помощник по миграции SQL Server для доступа.  
  
## <a name="uninstalling-ssma-for-access"></a>Удаление SSMA для доступа  
Удалите SSMA с помощью компонента " **Установка и удаление программ** " панели управления. Имейте в виду, что удаление программы не приводит к удалению файлов проекта SSMA или файлов журналов.  
  
**Удаление SSMA**  
  
1.  Щелкните **Пуск**, нажмите **Панель управления**, а затем **Установка и удаление программ**.  
  
2.  Выберите **Помощник по миграции Microsoft SQL Server для доступа**, а затем нажмите кнопку **Удалить**.  
  
## <a name="upgrading-to-a-later-version"></a>Обновление до более поздней версии  
Если требуется выполнить обновление до более поздней версии SSMA для доступа, необходимо сначала удалить SSMA для Access, а затем установить более новую версию. Чтобы завершить этот процесс, следуйте инструкциям в разделе Удаление SSMA для Access.  
  
При открытии проекта, созданного в более ранней версии SSMA для доступа, SSMA спрашивает, нужно ли преобразовать проект в более новую версию. Нажмите кнопку **Да** , чтобы работать с проектом в более новой версии SSMA.  
  
## <a name="see-also"></a>Дополнительно  
[Подготовка баз данных Access к миграции](preparing-access-databases-for-migration-accesstosql.md)  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Связывание приложений Access с SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  

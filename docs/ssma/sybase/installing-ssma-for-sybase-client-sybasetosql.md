---
title: Установка SSMA для клиента SAP ASE (SybaseToSQL) | Документация Майкрософт
description: Дополнительные сведения о предварительных требованиях для установки Помощник по миграции SQL Server (SSMA) для SAP адаптивного сервера Enterprise (ASE) и инструкции по установке.
ms.custom: ''
ms.date: 07/14/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5907a7cc5b93594beef8f7bd54f27f20b93fbb99
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87864861"
---
# <a name="installing-ssma-for-sap-ase-client-sybasetosql"></a>Установка SSMA для клиента SAP ASE (SybaseToSQL)

Клиент SSMA состоит из программных файлов, которые используются для подключения к серверу базы данных SAP адаптивного сервера предприятия (ASE) и к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , преобразованию объектов базы данных ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис или, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] а также [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] для переноса данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

В этом разделе приведены предварительные требования для установки и инструкции по установке SSMA.

## <a name="prerequisites"></a>Предварительные условия

SSMA предназначен для работы с SAP ASE 11.9.2 или более поздними версиями и всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.

- Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.
- Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)].NET Framework версии 4.7.2 или более поздней версии. Его можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Поставщик Sybase OLE DB/ADO.Net/ODBC и подключение к серверу базы данных SAP ASE, содержащему базы данных, которые необходимо перенести. Поставщики можно установить на носителе с продуктом SAP ASE. Дополнительные сведения о подключении см. [в статье подключение к SYBASE ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).
- Доступ к и достаточным разрешениям на компьютере, на котором размещен целевой экземпляр, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] котором будут перенесены объекты и данные базы данных. Дополнительные сведения см. в статьях [Подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).
- рекомендуется 4 ГБ ОЗУ.

## <a name="installing-the-ssma-for-sybase-client"></a>Установка клиента SSMA для Sybase

SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmaforsybase).

Чтобы установить клиент SSMA, выполните следующие действия.

1. Дважды щелкните **SSMAforSybase_*n*. msi**, где *n* — номер сборки.
2. На странице приветствия нажмите кнопку **Далее**.

   Если предварительные условия не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.

3. Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия соглашения**, а затем нажмите кнопку **Далее**.
4. На странице Выбор типа установки выберите вариант **Обычная**.
5. На странице **все готово для установки** можно включить или отключить данные телеметрии и автоматические проверки обновлений при каждом запуске средства. Нажмите кнопку **Установить**, чтобы начать установку.

> [!IMPORTANT]
> Удалите все предыдущие версии SSMA для Sybase перед установкой новой версии.

Расположение установки по умолчанию — `C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase`.

Помимо файлов программы SSMA, необходимо также установить пакет расширений SSMA для Sybase на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе Install SSMA Components on SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).

## <a name="see-also"></a>См. также

- [Установка компонентов SSMA в SQL Server](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
- [Миграция баз данных Sybase ASE в базу данных SQL Azure SQL Server](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)

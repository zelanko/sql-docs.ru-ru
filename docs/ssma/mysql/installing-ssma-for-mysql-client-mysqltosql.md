---
title: Установка SSMA для клиента MySQL (MySQLToSQL) | Документация Майкрософт
description: Дополнительные сведения о предварительных требованиях для установки Помощник по миграции SQL Server (SSMA) для клиента MySQL и инструкции по установке.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: d6bda2cad0761dbb53fcc4bb66d29829841f249d
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87824049"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>Установка SSMA для клиента MySQL (MySQLToSQL)

Клиент SSMA для MySQL состоит из программных файлов, которые выполняют следующие задачи:

- Подключитесь к базе данных MySQL.  
- Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .
- Преобразуйте объекты базы данных MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] объекты или.
- Загрузите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .
- Перенос данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

В этом разделе приведены необходимые условия для установки и инструкции по установке SSMA для клиента MySQL.

## <a name="prerequisites"></a>Предварительные условия

SSMA для MySQL предназначен для работы с MySQL 4,1 или более поздними версиями и всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или более поздней версии и [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.

- Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.
- Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4.7.2 или более поздняя. Его можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Драйвер MySQL ODBC 5,1 и подключение к базам данных MySQL, которые необходимо перенести. MySQL можно установить с веб-сайта MySQL. Дополнительные сведения о подключении см. [в разделе Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md).
- Доступ к и достаточным разрешениям на компьютере, на котором размещен целевой экземпляр, на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] котором будут перенесены объекты и данные базы данных. Дополнительные сведения см. [в разделе Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md).
- В случае с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] проектами доступ к экземпляру, на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] котором будут переноситься объекты и данные базы данных, имеет разрешение и достаточный уровень разрешений. Дополнительные сведения см. [в статье подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).
- рекомендуется 4 ГБ ОЗУ.

## <a name="installing-ssma-for-mysql-client"></a>Установка SSMA для клиента MySQL

SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmaformysql).

Чтобы установить клиент SSMA, выполните следующие действия.

1. Дважды щелкните **SSMAforMySQL_*n*. msi**, где *n* — номер сборки.
2. На странице **приветствия** нажмите кнопку **Далее**.

   Если необходимые компоненты не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Перед повторным запуском программы установки убедитесь, что установлены все необходимые компоненты.

3. Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия соглашения**, а затем нажмите кнопку **Далее**.
4. На странице **Выбор типа установки** выберите вариант **Обычная**.
5. На странице **все готово для установки** можно включить или отключить данные телеметрии и автоматические проверки обновлений при каждом запуске средства. Нажмите кнопку **Установить**, чтобы начать установку.

> [!IMPORTANT]
> Удалите все предыдущие версии SSMA для MySQL перед установкой новой версии.

Расположение установки по умолчанию — `C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL`.

## <a name="see-also"></a>См. также

- [Перенос баз данных MySQL в базу данных SQL Azure SQL Server](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  

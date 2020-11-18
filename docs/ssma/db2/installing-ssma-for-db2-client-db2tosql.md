---
title: Установка SSMA для клиента DB2 (DB2ToSQL) | Документация Майкрософт
description: Дополнительные сведения о предварительных требованиях для установки Помощник по миграции SQL Server (SSMA) для клиента DB2 и инструкции по установке.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: a223f5dbf6e100ac776e2f3aebad51c9bb885abf
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869612"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Установка SSMA для клиента DB2 (DB2ToSQL)

Клиент SSMA состоит из программных файлов, которые выполняют следующие задачи:

- Соединение с базой данных DB2
- Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
- Преобразование объектов базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис.
- Загрузите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Перенос данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

В этом разделе приведены предварительные требования для установки и инструкции по установке SSMA.

## <a name="prerequisites"></a>Предварительные требования

SSMA предназначен для работы с DB2 в z/OS версии 9,0 и 10,0, DB2 на LUW версии 9,8 и 10,1 или более поздних версиях, DB2 для версий 7,1 и более [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или более поздних версий.

Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.

- Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] Установщик Windows 3,1 или более поздних версий.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4.7.2 или более поздняя. Его можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Поставщик OLE DB для DB2 (Майкрософт) версии 5 или более поздней, а также подключение к базам данных DB2, которые требуется перенести.
- Доступ к и достаточным разрешениям на компьютере, на котором размещен целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или база данных SQL Azure, куда будут перенесены объекты и данные базы данных. Дополнительные сведения см. [в разделе Подключение к SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2tosql.md).
- рекомендуется 4 ГБ ОЗУ.

## <a name="microsoft-ole-db-provider-for-db2"></a>Поставщик Microsoft OLE DB для DB2

Чтобы скачать поставщик OLE DB для DB2 версии 6,0, перейдите в раздел [Microsoft® SQL Server® 2017 (пакет дополнительных компонентов)](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmafordb2).

Чтобы установить клиент SSMA, выполните следующие действия.

1. Дважды щелкните **SSMAforDB2_ *n*. msi**, где *n* — номер сборки.
2. На странице **приветствия** нажмите кнопку **Далее**.

   Если предварительные условия не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.

3. Прочтите лицензионное соглашение End-User. Если вы согласны, установите флажок **я принимаю условия соглашения**, а затем нажмите кнопку **Далее**.
4. На странице **Выбор типа установки** выберите вариант **Обычная**.
5. На странице **все готово для установки** можно включить или отключить данные телеметрии и автоматические проверки обновлений при каждом запуске средства. Нажмите кнопку **Установить**, чтобы начать установку.

> [!IMPORTANT]
> Удалите все предыдущие версии SSMA для DB2 перед установкой новой версии.

Расположение установки по умолчанию — `C:\Program Files\Microsoft SQL Server Migration Assistant for DB2`.

## <a name="see-also"></a>См. также статью

- [Установка компонентов SSMA на SQL Server](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)
- [Миграция баз данных DB2 в SQL Server](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)

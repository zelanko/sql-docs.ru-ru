---
title: Установка компонентов SSMA на SQL Server (OracleToSQL) | Документация Майкрософт
description: Узнайте, как установить пакет расширений SSMA и поставщики Oracle на компьютере, на котором выполняется SQL Server для поддержки преобразования базы данных Oracle.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing the extension pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 7acabfac10c3eb6e7afa1fbfbb2f546b0ae4137d
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006436"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Установка компонентов SSMA на SQL Server (OracleToSQL)

Помимо установки SSMA, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . К этим компонентам относится пакет расширений SSMA, который поддерживает миграцию данных, и поставщики Oracle для обеспечения подключения между серверами.

## <a name="ssma-for-oracle-extension-pack"></a>SSMA для пакета расширений Oracle

Пакет расширений SSMA добавляет базы данных **сисдб** и **ссматестердб** в указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . База данных **сисдб** содержит таблицы и хранимые процедуры, необходимые для переноса данных, и определяемые пользователем функции, имитирующие системные функции Oracle. База данных **ссматестердб** содержит таблицы и процедуры, необходимые компоненту тестера.

Кроме того, при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда для переноса данных используется модуль миграции данных на стороне сервера.

### <a name="prerequisites"></a>Предварительные условия

Перед установкой SSMA для компонентов сервера Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Убедитесь, что система соответствует следующим требованиям.

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр установлен.
- Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4.7.2 или более поздняя. Его можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Поставщик OLE DB для Oracle (если используется OLE DB) и подключение к базе данных Oracle, которую требуется перенести. Поставщики можно установить с носителя продукта Oracle или с веб-сайта Oracle.
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Служба браузера должна быть запущена во время установки. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Службу браузера можно отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после установки.

  > [!NOTE]
  > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Служба браузера запущена, но список экземпляров в программе установки по-прежнему не отображается, необходимо разблокировать UDP-порт 1434. Вы можете использовать брандмауэр Windows, чтобы временно разблокировать порт, или временно отключить брандмауэр Windows. Также может потребоваться временное отключение антивирусного по. После установки обязательно включите брандмауэры и антивирусное по.

### <a name="installing-the-extension-pack"></a>Установка пакета расширений

Пакет расширений можно установить в любое время перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!IMPORTANT]
> Чтобы установить пакет расширений, необходимо быть членом роли сервера **sysadmin** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Чтобы установить пакет расширений, выполните следующие действия.

1. Скопируйте **SSMAforOracleExtensionPack_*n*. msi** (где *n* — номер сборки) на компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
2. Дважды щелкните **SSMAforOracleExtensionPack_*n*. msi**.
3. На странице **приветствия** нажмите кнопку **Далее**.
4. На странице Лицензионное **соглашение** ознакомьтесь с лицензионным соглашением. Если вы согласны, выберите параметр **я принимаю условия соглашения** , а затем нажмите кнопку **Далее**.
5. На странице **Выбор типа установки** выберите вариант **Обычная**.
6. На странице **Все готово для установки** нажмите кнопку **Установить**.
7. На странице **завершено первое действие установки** нажмите кнопку **Далее**.
  
   Откроется новое диалоговое окно. Выберите тип пакета расширений.
  
8. Выберите нужный тип установки и нажмите кнопку **Далее**.

   > [!IMPORTANT]
   > Параметр Remote следует использовать только при установке пакета расширения на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютере под управлением Linux или при нацеливании [!INCLUDE[ssAzureMi](../../includes/ssazuremi_md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] При установке в Windows всегда должен быть установлен пакет расширений локально. [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и Azure синапсе Analytics не поддерживают пакет расширений.

   Если пакет расширений устанавливается на локальном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляре, то на следующей странице можно будет выбрать локальный экземпляр, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в который будут перенесены схемы Oracle. Выберите экземпляр в раскрывающемся списке и нажмите кнопку **Далее**.

   Имя экземпляра по умолчанию совпадает с именем компьютера. За именованными экземплярами будет следовать обратная косая черта и имя экземпляра.

9. На странице Подключение выберите метод проверки подлинности и нажмите кнопку **Далее**.

   При проверке подлинности Windows будут использоваться учетные данные Windows для входа в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе проверки подлинности сервера необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.

10. На следующем шаге необходимо задать пароль для главного ключа, который будет использоваться для шифрования любых конфиденциальных данных, хранящихся в базе данных пакета расширений при переносе данных на стороне сервера. Укажите надежный пароль и нажмите кнопку **Далее**.

11. На следующей странице выберите **установить служебные программы база данных *n* и установите библиотеки пакетов расширений**, где *n* — номер версии. Если вы планируете использовать функцию "тест-инженер", установите флажок **установить базу данных тестировщика** и нажмите кнопку **Далее**.

    База данных **сисдб** создается с таблицами и хранимыми процедурами, необходимыми для переноса данных (используя модуль миграции данных на стороне сервера) в этой базе данных.

    Если установлен флажок **установить базу данных тестировщика** , будет создана база данных **ссматестердб** .

12. После завершения установки появится запрос на подтверждение установки служебной базы данных на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выберите **Да**, а затем нажмите кнопку **Далее**или закрыть мастер, выберите **нет** и нажмите кнопку **выход**.

13. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью `sqlcmd` программы выполните следующий скрипт, чтобы включить CLR:

    ```sql
    sp_configure 'clr enabled', 1
    GO
    RECONFIGURE
    GO
    ```

    Если среда CLR не включена, при подключении SSMA к выполните следующее сообщение об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :

    > SSMA не удалось получить сведения о версии сборки пакета расширений. Переустановите пакет расширений на сервере базы данных.

### <a name="sql-server-database-objects"></a>SQL Server объекты базы данных

После установки пакета расширений в базе данных **сисдб** появляется таблица **ssma_oracle. bcp _migration_packages** .

Каждый раз при миграции данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Задание агента. Эти задания называются **ssma_oracle пакет переноса данных {GUID}** и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] узле агент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папке задания.

## <a name="see-also"></a>См. также статью

- [Установка SSMA для клиента Oracle](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)
- [Миграция баз данных Oracle в SQL Server](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)

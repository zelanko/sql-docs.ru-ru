---
title: "Перенос схемы Oracle HR в SQL Server для Linux | Документы Microsoft"
description: "Преобразовать образец схемы Oracle для SQL Server в Linux"
author: edmacauley
ms.author: edmacauley
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: d49a98dd9268a2ea532b0b960bb0740580ccee69
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Перенос схемы Oracle для 2017 г. SQL Server в Linux с SQL Server Migration Assistant

В этом учебнике используется SQL Server Migration Assistant (SSMA) для Oracle в Windows, чтобы преобразовать образец Oracle **HR** схемы для [2017 г. SQL Server в Linux](../../linux/sql-server-linux-overview.md).

> [!div class="checklist"]
> * Загрузите и установите SSMA для Windows
> * Создание проекта SSMA для управления миграцией
> * Соединение с Oracle
> * Запустите отчет о миграции
> * Образец схемы HR
> * Перенос данных

## <a name="prerequisites"></a>Предварительные требования

- Экземпляр Oracle 12c (12.2.0.1.0) с **HR** установлена схема
- Рабочий экземпляр SQL Server в Linux

> [!NOTE]
> Можно использовать те же действия для целевого SQL Server в Windows, но необходимо выбрать Windows в **Миграция в** параметр проекта.

## <a name="download-and-install-ssma-for-oracle"></a>Загрузите и установите SSMA для Oracle

Существует несколько выпусков SQL Server Migration Assistant, в зависимости от базы данных-источника.  Загрузить текущую версию [SQL Server Migration Assistant для Oracle](http://aka.ms/ssmafororacle) и установите его с помощью инструкциям, приведенным на странице загрузки.

> [!NOTE]
> В настоящее время **SSMA для пакета расширения Oracle** не поддерживается в Linux, но нет необходимости в этом учебнике.

## <a name="create-and-set-up-project"></a>Создание и настройка проекта

Для создания нового проекта SSMA, выполните следующие действия:

1. SSMA для Oracle и задается **новый проект** из **файл** меню.

1. Укажите имя проекта.

1. Выберите «2017 г. (Linux) — Предварительная версия SQL Server» в **Миграция в** поле.

SSMA для Oracle не использует образец схемы Oracle по умолчанию. Чтобы включить схему HR, выполните следующие действия:

1. SSMA, выберите **средства** меню.

1. Выберите **параметры проекта по умолчанию**, а затем выберите **загрузке системных объектов**.

1. Убедитесь, что **HR** проверяется и выберите **ОК**.

## <a name="connect-to-oracle"></a>Соединение с Oracle

Затем подключения SSMA с базой данных Oracle.

1. На панели инструментов щелкните **подключение к Oracle**.

1. Введите имя сервера, порт, Oracle SID, имя пользователя и пароль.

   ![Соединение с Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. Затем нажмите кнопку **Подключить**. Через несколько секунд SSMA для Oracle подключается к базе данных и читает его метаданные.

## <a name="create-a-report"></a>Создание отчета

Чтобы создать отчет о миграции, выполните следующие действия.

1. В **обозреватель метаданных Oracle**, разверните узел сервера.

1. Разверните **схемы**, щелкните правой кнопкой мыши **HR**и выберите **создать отчет**.

   ![Обозреватель метаданных Oracle Создание отчета](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Откроется новое окно браузера с отчетом, в которой перечислены все предупреждения и ошибки, связанные с преобразованием.

   > [!NOTE]
   > Не нужно выполнять никаких действий с этим списком для этого учебника. Если выполнить эти действия для базы данных Oracle, следует просматривать отчет, чтобы решить проблемы преобразования важные для вашей базы данных.

   ![Отчет о миграции образца](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Затем выберите **подключение к SQL Server** и введите соответствующие сведения о подключении.  Если используется имя базы данных, которая еще не существует, создает эту SSMA для Oracle.

![Подключение к SQL Server](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Преобразовать схему

Щелкните правой кнопкой мыши **HR** в **обозреватель метаданных Oracle**и выберите Преобразование схемы.

![Преобразовать схему](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Синхронизация базы данных

После этого синхронизация базы данных.

1. После завершения преобразования с помощью **обозреватель метаданных SQL Server** перейдите к базе данных, созданной на предыдущем шаге.

1. Щелкните правой кнопкой мыши на базу данных, выберите **синхронизации с базой данных**, а затем нажмите кнопку ОК.

   ![Синхронизации с базой данных](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>Перенос данных

Последним шагом является перенос данных.

1. В **обозреватель метаданных Oracle**, щелкните правой кнопкой мыши **HR**и выберите **переноса данных**.

1. Шаги переноса данных необходимо повторно ввести учетные данные Oracle и SQL Server.

1. После завершения просмотрите отчет о миграции данных, который должен выглядеть примерно следующим образом:

   ![Отчет о миграции данных](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Следующие шаги

Для более сложная схема Orcale процесс преобразования организуется больше времени, тестирования и возможные изменения для клиентских приложений. Этот учебник призван показывают, как использовать SSMA для Oracle как часть общего процесса миграции.

В этом учебнике вы узнали, как:
> [!div class="checklist"]
> * Установка SSMA в Windows
> * Создание нового проекта SSMA
> * Оценить и запустить миграцию из Oracle

Затем изучите другие способы использования SSMA:

> [!div class="nextstepaction"]
>[Документация по SQL Server Migration Assistant](../sql-server-migration-assistant.md)


---
title: Перенос схемы Oracle HR в SQL Server в Linux | Документация Майкрософт
description: Преобразовать образец схемы Oracle в SQL Server в Linux
author: shamikg
ms.author: shamikg
manager: v-thobro
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: ssma
ms.openlocfilehash: 312797b2b883f764fc65588e72cd67d7227e327a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62629803"
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Перенос схемы Oracle для SQL Server 2017 на платформе Linux с помощью SQL Server Migration Assistant

В этом учебнике используется SQL Server Migration Assistant (SSMA) для Oracle в Windows для преобразования образец Oracle **HR** схемы для [SQL Server 2017 в Linux](../../linux/sql-server-linux-overview.md).

> [!div class="checklist"]
> * Скачать и установить SSMA на Windows
> * Создание проекта SSMA для управления миграцией
> * Соединение с Oracle
> * Запустите отчет о миграции
> * Преобразование примера схемы HR
> * Перенос данных

## <a name="prerequisites"></a>предварительные требования

- Экземпляр Oracle 12c (12.2.0.1.0) с **HR** установлена схема
- Рабочий экземпляр SQL Server в Linux

> [!NOTE]
> Те же действия можно использовать для целевого SQL Server в Windows, но необходимо выбрать Windows в **Миграция в** проекта параметр.

## <a name="download-and-install-ssma-for-oracle"></a>Загрузить и установить SSMA для Oracle

Существует несколько выпусков SQL Server Migration Assistant, в зависимости от вашей базы данных-источника.  Загрузить текущую версию [SQL Server Migration Assistant для Oracle](https://aka.ms/ssmafororacle) и установите его, следуя инструкциям на странице загрузки.

> [!NOTE]
> В настоящее время **SSMA для Oracle Extension Pack** не поддерживается на платформе Linux, но нет необходимости в этом руководстве.

## <a name="create-and-set-up-project"></a>Создание и настройка проекта

Для создания нового проекта SSMA, следуйте инструкциям ниже:

1. Откройте SSMA для Oracle и выберите **новый проект** из **файл** меню.

1. Присвойте проекту имя.

1. Выберите «SQL Server 2017 (Linux) — Предварительная версия» в **Миграция в** поля.

SSMA для Oracle не использует образец схемы Oracle по умолчанию. Чтобы включить схему HR, следуйте инструкциям ниже:

1. В SSMA, выберите **средства** меню.

1. Выберите **параметры проекта по умолчанию**, а затем выберите **Загрузка системных объектов**.

1. Убедитесь, что **HR** проверяется и выберите **ОК**.

## <a name="connect-to-oracle"></a>Соединение с Oracle

Затем подключения SSMA для Oracle.

1. На панели инструментов щелкните **подключение к Oracle**.

1. Введите имя сервера, порт, ИД безопасности Oracle, имя пользователя и пароль.

   ![Соединение с Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. Затем нажмите кнопку **Подключить**. Через несколько секунд SSMA для Oracle подключается к базе данных и считывает его метаданные.

## <a name="create-a-report"></a>Создание отчета

Чтобы создать отчет о миграции, выполните следующие действия.

1. В **обозреватель метаданных Oracle**, разверните узел сервера.

1. Разверните **схемы**, щелкните правой кнопкой мыши **HR**и выберите **создать отчет**.

   ![Обозреватель метаданных Oracle Создание отчета](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Откроется новое окно браузера с отчет, перечисляющий все предупреждения и ошибки, связанные с преобразованием.

   > [!NOTE]
   > Не нужно ничего делать с этим списком для этого руководства. Если выполнить эти шаги для базы данных Oracle, следует просмотреть отчет для устранения возможных проблем преобразования важных для вашей базы данных.

   ![Отчет о миграции образца](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Далее выберите **подключение к SQL Server** и введите соответствующие сведения о подключении.  Если вы используете имя базы данных, который еще не существует, создает эту SSMA для Oracle.

![Подключение к SQL Server](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Преобразовать схему

Щелкните правой кнопкой мыши **HR** в **обозреватель метаданных Oracle**и выберите пункт Преобразовать схемы.

![Преобразовать схему](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Синхронизации базы данных

Затем можно синхронизировать базы данных.

1. После завершения преобразования использовать **обозреватель метаданных SQL Server** перейдите к базе данных, созданного на предыдущем шаге.

1. Щелкните правой кнопкой мыши в вашей базе данных, выберите **синхронизация с базой данных**, а затем нажмите кнопку ОК.

   ![Синхронизировать с базой данных](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>Перенос данных

Последним шагом является перенос данных.

1. В **обозреватель метаданных Oracle**, щелкните правой кнопкой мыши **HR**и выберите **переноса данных**.

1. На этапе миграции данных необходимо повторно ввести учетные данные Oracle и SQL Server.

1. После завершения просмотрите отчет о миграции данных, который должен выглядеть как на следующем снимке экрана:

   ![Отчет о миграции данных](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Следующие шаги

Для более сложная схема Orcale процесс преобразования будет включать в себя больше времени, тестирование и возможные изменения для клиентских приложений. Цель этого руководства — Показать, как использовать SSMA для Oracle как часть общего процесса миграции.

В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Установка SSMA на Windows
> * Создание нового проекта SSMA
> * Оценка и выполнять миграцию из Oracle

Затем изучите другие способы использования SSMA.

> [!div class="nextstepaction"]
>[Документация по SQL Server Migration Assistant](../sql-server-migration-assistant.md)

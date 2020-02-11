---
title: Перенос SQL Server в базу данных SQL Azure с помощью Помощник по миграции данных
description: Узнайте, как использовать Помощник по миграции данных для переноса локальной SQL Server в базу данных SQL Azure.
ms.date: 07/15/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: cc87b541b2b6ebf2f6a9068ba35ae0f62f8e9988
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056614"
---
# <a name="migrate-on-premises-sql-server-or-sql-server-on-azure-vms-to-azure-sql-database-using-the-data-migration-assistant"></a>Миграция локальных SQL Server или SQL Server на виртуальные машины Azure в базу данных SQL Azure с помощью Помощник по миграции данных

Помощник по миграции данных обеспечивает простую оценку SQL Server в локальной среде и обновления до более поздних версий SQL Server или миграций для SQL Server на виртуальных машинах Azure или базе данных SQL Azure.

В этой статье приведены пошаговые инструкции по миграции SQL Server локальной среды в базу данных SQL Azure с помощью Помощник по миграции данных.

## <a name="create-a-new-migration-project"></a>Создание проекта миграции

1. На левой панели выберите **создать** (+), а затем выберите тип проекта **Миграция** .

2. Задайте для параметра Тип источника значение **SQL Server** , а для параметра Тип целевого сервера — **база данных SQL Azure**.

3. Нажмите кнопку **Создать**.

   ![Создание проекта миграции](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>Укажите исходный сервер и базу данных

1. Для источника в разделе **Подключение к исходному серверу**в текстовом поле **имя сервера** введите имя исходного SQL Server экземпляра.

2. Выберите **тип проверки подлинности** , поддерживаемый экземпляром SQL Server источника.

   > [!NOTE]
   > Рекомендуется зашифровать подключение, установив флажок **Шифровать соединение** в разделе **Подключение попертиес**.

    ![Выбор исходного сервера](../dma/media/select-source-server.png)

3. Выберите **Подключиться**.

4. Выберите одну базу данных-источник для переноса в базу данных SQL Azure.

   > [!NOTE]
   > Если вы хотите оценить базу данных и просмотреть и применить Рекомендуемые исправления перед миграцией, установите флажок **оценить базу данных перед миграцией?** .

    ![Выбор базы данных источника](../dma/media/select-source-database.png)

5. Выберите **Далее**.

## <a name="specify-the-target-server-and-database"></a>Укажите целевой сервер и базу данных

1. Для целевого объекта в разделе **Подключение к целевому серверу**в текстовом поле **имя сервера** введите имя экземпляра базы данных SQL Azure. 

2. Выберите **тип проверки подлинности** , поддерживаемый целевым экземпляром базы данных SQL Azure.

   > [!NOTE]
   > Рекомендуется зашифровать подключение, установив флажок **Шифровать соединение** в разделе **Подключение попертиес**.

     ![Выбор целевого сервера](../dma/media/select-target-server.png)

3. Выберите **Подключиться**.

4. Выберите одну целевую базу данных для миграции.

   > [!NOTE]
   > Если планируется миграция пользователей Windows, в текстовом поле **целевой домен имя внешнего пользователя** убедитесь, что имя внешнего пользователя целевой указано правильно.

    ![Выбор целевой базы данных](../dma/media/select-target-database.png)

5. Выберите **Далее**.

## <a name="select-schema-objects"></a>Выбор объектов схемы

1. Выберите объекты схемы из базы данных источника, которые необходимо перенести в базу данных SQL Azure.

    ![Выбор объектов схемы](../dma/media/select-schema-objects.png)

       > [!NOTE]
       > Some of the objects that cannot be converted as-is are presented with automatic fix opportunities. Clicking these objects on the left pane displays the suggested fixes on the right pane. Review the fixes and choose to either apply or ignore all changes, object by object. Note that applying or ignoring all changes for one object does not affect changes to other database objects. Statements that cannot be converted or automatically fixed are reproduced to the target database and commented.

    ![Предлагаемое исправление](../dma/media/suggested-fix.png)

2. Выберите **Общий скрипт SQL**.

3. Проверьте созданный скрипт.

    ![Созданный скрипт](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>Развертывание схемы

1. Выберите **развернуть схему**.

2. Проверьте результаты развертывания схемы.

    ![Результаты развертывания схемы](../dma/media/schema-deployment-results.png)

3. Выберите **Миграция данных** , чтобы начать процесс миграции данных.

4. Выберите таблицы с данными, которые необходимо перенести.

    ![Выбор таблиц для миграции](../dma/media/select-tables-to-migrate.png) 

5. Выберите **начать миграцию данных**.

На последнем экране отображается общее состояние.

   ![Состояние миграции](../dma/media/migration-status.png) 

## <a name="see-also"></a>См. также раздел

* [Помощник по миграции данных (DMA)](../dma/dma-overview.md)
* [Помощник по миграции данных: параметры конфигурации](../dma/dma-configurationsettings.md)
* [Помощник по миграции данных: рекомендации](../dma/dma-bestpractices.md)

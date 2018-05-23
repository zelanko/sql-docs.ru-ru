---
title: Планирование выполнения пакетов SQL Server Integration Services в Azure с помощью SQL Server Management Studio | Документы Майкрософт
description: Описывается, как запланировать выполнение пакетов SQL Server Integration Services, развернутых в базе данных SQL Azure, с помощью команды "Расписание" в SQL Server Management Studio (SSMS).
ms.date: 05/09/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 72b20d4d42517555449f639cee398db4363d5735
ms.sourcegitcommit: 0cc2cb281e467a13a76174e0d9afbdcf4ccddc29
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2018
---
# <a name="schedule-the-execution-of-an-ssis-package-in-azure-with-sql-server-management-studio-ssms"></a>Планирование выполнения пакета SQL Server Integration Services в Azure с помощью SQL Server Management Studio (SSMS)

Среда SQL Server Management Studio (SSMS) предоставляет функцию для планирования выполнения пакетов SQL Server Integration Services, развернутых в базе данных SQL Azure. В локальной системе SQL Server и управляемом экземпляре базы данных SQL Azure (предварительная версия) в качестве полноценных планировщиков заданий SQL Server Integration Services используются агент SQL Server и агент управляемого экземпляра соответственно. В свою очередь, база данных SQL Azure не имеет полноценного встроенного планировщика заданий SQL Server Integration Services. Функция SSMS, описываемая в этой статье, предоставляет пользовательский интерфейс для планирования выполнения пакетов, развернутых в базе данных SQL, который похож на аналогичный интерфейс агента SQL Server.

Если база данных каталога SQL Server Integration Services (`SSISDB`) размещается в базе данных SQL, с помощью этой функции SSMS можно создать конвейеры, действия и триггеры фабрики данных, необходимые для планирования пакетов SQL Server Integration Services. Затем можно изменять и расширять эти объекты в фабрике данных.

При планировании выполнения пакета в среде SSMS она автоматически создает три объекта фабрики данных, имена которых зависят от выбранного пакета и метки времени. Например, если пакет SQL Server Integration Services имеет имя **MyPackage**, SSMS создает в фабрике данных такие объекты:

| Объект | Имя |
|---|---|
| Pipeline | **Pipeline_MyPackage_2018-05-08T09_00_00Z** |
| Действие "Выполнение пакета SSIS" | **Activity_MyPackage_2018-05-08T09_00_00Z** |
| Триггер | **Trigger_MyPackage_2018-05-08T09_00_00Z** |
|||

## <a name="prerequisites"></a>предварительные требования

Для функции, описываемой в этой статье, требуется SQL Server Management Studio версии 17.7 или более поздней. Чтобы получить последнюю версию SSMS, перейдите на страницу [скачивания SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="schedule-a-package-in-ssms"></a>Планирование выполнения пакета в SSMS

1. В SSMS в обозревателе объектов выберите базу данных SSISDB, папку, проект, а затем пакет. Щелкните пакет правой кнопкой мыши и выберите пункт **Расписание**.

    ![Выберите пакет для планирования.](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image1-schedule.png)

2. Открывает диалоговое окно **Создание расписания**. На странице **Общие** диалогового окна **Создание расписания** укажите имя и описание нового запланированного задания.

    ![Страница "Общие" диалогового окна "Создание расписания"](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image2-new-schedule.png)

3. На странице **Пакет** диалогового окна **Создание расписания** выберите необязательные параметры времени выполнения и среду выполнения.

    ![Страница "Пакет" диалогового окна "Создание расписания"](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image3-new-schedule2.png)

4. На странице **Расписание** диалогового окна **Создание расписания** укажите параметры расписания, такие как частота, время суток и длительность.

    ![Страница "Расписание" диалогового окна "Создание расписания"](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image4-new-schedule3.png)

5. Когда вы завершите создание задания в диалоговом окне **Создание расписания**, появится напоминание об объектах, которые среда SSMS создаст в фабрике данных. Если в диалоговом окне подтверждения выбрать вариант **Да**, новый конвейер фабрики данных откроется на портале Azure, где его можно просмотреть и настроить.

    ![Подтверждение создания расписания](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image5-confirmation.png)

6. Чтобы настроить триггер расписания, в меню **Триггер** выберите пункт **Создать или изменить**.

    ![При необходимости измените новый конвейер.](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image6-edit.png)

    Откроется колонка **Изменить триггер**, в которой можно настроить параметры расписания.

    ![Изменить триггер](media/ssis-azure-schedule-packages-ssms/schedule-ssms-image7-edit2.png)

## <a name="next-steps"></a>Следующие шаги

Сведения о других способах запланировать выполнение пакета SQL Server Integration Services см. в статье [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).

Дополнительные сведения о конвейерах, действиях и триггерах фабрики данных Azure см. в следующих статьях:
-   [Конвейеры и действия в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities)
-   [Выполнение конвейера и триггеры в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers)

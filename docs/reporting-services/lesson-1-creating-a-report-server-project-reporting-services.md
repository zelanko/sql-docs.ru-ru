---
title: Урок 1. Создание проекта сервера отчетов | Документация Майкрософт
description: В этом уроке вы создадите проект сервера отчетов и RDL-файл определения отчета с помощью конструктора отчетов.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: db412b18a0189f9f68caff79f8e904db5424d673
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244315"
---
# <a name="lesson-1-create-a-report-server-project-reporting-services"></a>Урок 1. Создание проекта сервера отчетов (службы Reporting Services)

В этом уроке вы создадите *проект сервера отчетов* и *RDL-файл определения отчета* с помощью *конструктора отчетов*.

> [!NOTE]
> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] представляет собой среду [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания решений бизнес-аналитики. SSDT содержит среду разработки, (конструктор отчетов), в которой можно открывать, изменять, просматривать, сохранять и развертывать определения отчетов [!INCLUDE[ssrsnoversion_md](../includes/ssrsnoversion-md.md)] с разбивкой на страницы, общие источники данных, общие наборы данных и элементы отчетов.

При создании отчетов с помощью конструктора отчетов он создает проект сервера отчетов, который содержит файлы отчетов и других ресурсов, которые нужны для этих отчетов.

## <a name="to-create-a-report-server-project"></a>Создание проекта сервера отчетов
  
1. В меню **Файл** выберите пункт **Создать** > **Проект**.  

    ![ssrs-ssdt-file-01-new-project](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
2. В крайнем левом столбце в разделе **Установленные** выберите **Службы Reporting Services**. В некоторых случаях этот пункт может оказаться в группе **Бизнес-аналитика**.

    ![select-report-server-project-template](../reporting-services/media/lesson-1-creating-a-report-server-project-reporting-services/select-report-server-project-template.png)

    > [!IMPORTANT]
    > Если вы работаете в Visual Studio и не видите служб Reporting Services в левом столбце, добавьте конструктор отчетов, установив рабочую нагрузку SSDT. Из меню **Средства** выберите **Получить средства и компоненты...** , а затем в отображаемых рабочих нагрузках выберите **SQL Server Data Tools**. Если вы не видите объекты служб Reporting Services в центральном столбце, добавьте расширения служб Reporting Services. Откройте меню **Средства** и выберите **Расширения и обновления** > **В сети**. В центральном столбце выберите **Проекты Microsoft Reporting Services** > **Скачать** из отображаемого списка расширений. Сведения об SQL Server Data Tools (SSDT) см. [в этой статье](../ssdt/download-sql-server-data-tools-ssdt.md).

3. Выберите значок **Проект сервера отчетов** &nbsp;&nbsp;![ssrs_ssdt_report_server_project](media/ssrs-ssdt-report-server-project.png) &nbsp;&nbsp;в центральном столбце диалогового окна **Новый проект**.

4. В текстовом поле **Имя** введите имя проекта "Tutorial" (Обучение). По умолчанию текстовое поле **Расположение** отображает путь к папке Documents\Visual Studio 20xx\Projects\". Конструктор отчетов создаст в этой папке вложенную папку Tutorial и разместит в ней проект Tutorial. Если этот проект не принадлежит решению VS, то VS дополнительно создаст файл решения (.sln).

5. Чтобы создать проект, щелкните **ОК**. Проект Tutorial отобразится в области **обозревателя решений** справа.
  
## <a name="creating-a-report-definition-file-rdl"></a>Создание файла определения отчета (RDL)  
  
1. В области **обозревателя решений** щелкните правой кнопкой мыши папку **Reports** (Отчеты). Если область **обозревателя решений** не отображается, в меню **Вид** выберите пункт **Обозреватель решений**.

2. Щелкните **Добавить** > **Новый элемент**.

    ![ssrs_ssdt_add_report](../reporting-services/media/ssrs-ssdt-add-report.png)

3. В окне **Добавление нового элемента** щелкните значок **Отчет**.

4. Введите "Sales Orders.rdl" в текстовое поле **Имя**.

5. Нажмите кнопку **Добавить** справа внизу в диалоговом окне **Добавление нового элемента**, чтобы завершить процесс. Конструктор отчетов откроет и отобразит в представлении конструктора новый файл отчета Sales Orders.

    ![ssrs-ssdt-01-new-report-designer](media/ssrs-ssdt-01-new-report-designer.png)

## <a name="next-steps"></a>Дальнейшие действия

Итак, вы создали проект отчета Tutorial и отчет Sales Orders. В следующих уроках вы научитесь выполнять такие действия:

- настройка источника данных для отчета;
- создание набора данных из источника данных;
- разработка и форматирование макета отчета.

Переходите к статье [Занятие 2. Задание информации о соединении (службы Reporting Services)](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).

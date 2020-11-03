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
ms.openlocfilehash: ac84fb8cf355103b28fbac8f5411943aa4ee51a8
ms.sourcegitcommit: 22e97435c8b692f7612c4a6d3fe9e9baeaecbb94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92679052"
---
# <a name="lesson-1-create-a-report-server-project-reporting-services"></a>Урок 1. Создание проекта сервера отчетов (службы Reporting Services)

В этом уроке вы создадите *проект сервера отчетов* и *RDL-файл определения отчета* с помощью *конструктора отчетов*.

> [!NOTE]
> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] представляет собой среду [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания решений бизнес-аналитики. SSDT содержит среду разработки, (конструктор отчетов), в которой можно открывать, изменять, просматривать, сохранять и развертывать определения отчетов [!INCLUDE[ssrsnoversion_md](../includes/ssrsnoversion-md.md)] с разбивкой на страницы, общие источники данных, общие наборы данных и элементы отчетов.

При создании отчетов с помощью конструктора отчетов он создает проект сервера отчетов, который содержит файлы отчетов и других ресурсов, которые нужны для этих отчетов.

## <a name="to-create-a-report-server-project"></a>Создание проекта сервера отчетов
  
1. В меню **Файл** выберите пункт **Создать** > **Проект**.  

    ![Снимок экрана: интерфейс Visual Studio с выбранным пунктом меню "Файл > Создать > Проект".](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
2. В крайнем левом столбце в разделе **Установленные** выберите **Службы Reporting Services**. В некоторых случаях этот пункт может оказаться в группе **Бизнес-аналитика**.

    ![Снимок экрана: диалоговое окно "Создание проекта" с выбранными службами Reporting Services и выделенным шаблоном "Проект сервера отчетов".](../reporting-services/media/lesson-1-creating-a-report-server-project-reporting-services/select-report-server-project-template.png)

    > [!IMPORTANT]
    > Если вы работаете в Visual Studio и не видите служб Reporting Services в левом столбце, добавьте конструктор отчетов, установив рабочую нагрузку SSDT. Из меню **Средства** выберите **Получить средства и компоненты...** , а затем в отображаемых рабочих нагрузках выберите **SQL Server Data Tools**. Если вы не видите объекты служб Reporting Services в центральном столбце, добавьте расширения служб Reporting Services. Откройте меню **Средства** и выберите **Расширения и обновления** > **В сети**. В центральном столбце выберите **Проекты Microsoft Reporting Services** > **Скачать** из отображаемого списка расширений. Сведения об SQL Server Data Tools (SSDT) см. [в этой статье](../ssdt/download-sql-server-data-tools-ssdt.md). Если предыдущие шаги не помогли устранить проблему в Visual Studio 2019, попробуйте установить [расширение проекта службы Microsoft Reporting Service](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio).


3. Выберите значок **Проект сервера отчетов** &nbsp;&nbsp;![ssrs_ssdt_report_server_project](media/ssrs-ssdt-report-server-project.png) &nbsp;&nbsp;в центральном столбце диалогового окна **Новый проект**.

4. В текстовом поле **Имя** введите имя проекта "Tutorial" (Обучение). По умолчанию текстовое поле **Расположение** отображает путь к папке Documents\Visual Studio 20xx\Projects\". Конструктор отчетов создаст в этой папке вложенную папку Tutorial и разместит в ней проект Tutorial. Если этот проект не принадлежит решению VS, то VS дополнительно создаст файл решения (.sln).

5. Чтобы создать проект, щелкните **ОК**. Проект Tutorial отобразится в области **обозревателя решений** справа.
  
## <a name="creating-a-report-definition-file-rdl"></a>Создание файла определения отчета (RDL)  
  
1. В области **обозревателя решений** щелкните правой кнопкой мыши папку **Reports** (Отчеты). Если область **обозревателя решений** не отображается, в меню **Вид** выберите пункт **Обозреватель решений**.

2. Щелкните **Добавить** > **Новый элемент**.

    ![Снимок экрана: обозреватель решений с выбранным пунктом меню "Отчеты > Добавить > Новый элемент".](../reporting-services/media/ssrs-ssdt-add-report.png)

3. В окне **Добавление нового элемента** щелкните значок **Отчет**.

4. Введите "Sales Orders.rdl" в текстовое поле **Имя**.

5. Нажмите кнопку **Добавить** справа внизу в диалоговом окне **Добавление нового элемента** , чтобы завершить процесс. Конструктор отчетов откроет и отобразит в представлении конструктора новый файл отчета Sales Orders.

    ![Снимок экрана: интерфейс Visual Studio с конструктором отчетов и отчетом Sales Orders в представлении конструирования.](media/ssrs-ssdt-01-new-report-designer.png)

## <a name="next-steps"></a>Дальнейшие шаги

Итак, вы создали проект отчета Tutorial и отчет Sales Orders. В следующих уроках вы научитесь выполнять такие действия:

- настройка источника данных для отчета;
- создание набора данных из источника данных;
- разработка и форматирование макета отчета.

Перейти к уроку 2 [Задание информации о соединении (службы Reporting Services)](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).

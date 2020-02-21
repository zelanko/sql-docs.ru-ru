---
title: Урок 2. Задание информации о подключении (службы Reporting Services) | Документация Майкрософт
description: В этом уроке вы определите источник данных, то есть настроите сведения о подключении для доступа отчета к данным из реляционной базы данных или других источников.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9d4e12a0322a35e96bd930c4fa6f1f852daf2bdd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75258464"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Урок 2. Задание информации о подключении (службы Reporting Services)

В уроке 1 вы добавили отчет с разбиением на страницы [!INCLUDE[ssrsnoversion-md](../includes/ssrsnoversion-md.md)] к проекту Tutorial.
  
В этом уроке вы определите *источник данных*, то есть настроите сведения о подключении для доступа отчета к данным из реляционной базы данных или других источников.

Для этого отчета вы добавите в качестве источника данных пример базы данных AdventureWorks2016. В руководстве предполагается, что эта база данных размещена в экземпляре по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)], который установлен на локальном компьютере.  

## <a name="to-set-up-a-connection"></a>Настройка соединения  

1. На панели **Данные отчета** щелкните **Создать** > **Источник данных**. Если область **Данные отчета** не отображается, в меню **Вид** выберите пункт **Данные отчета**.

    ![ssrs-table-tutorial-2-new-data-source](media/ssrs-table-tutorial-2-new-data-source.png)

    Откроется диалоговое окно **Свойства источника данных** с разделом **Общие**.

    ![Диалоговое окно "Свойства источника данных"](media/lesson-2-specifying-connection-information-reporting-services/vs-datasource-connection-properties-dialog-box.png)

2. В текстовом поле **Имя** введите AdventureWorks2016.

3. Выберите переключатель **Внедренное соединение**.

4. В раскрывающемся списке **Тип** выберите "Microsoft SQL Server".
  
5. В текстовом поле **Строка подключения** введите следующую строку:

    `Data source=localhost; initial catalog=AdventureWorks2016`

    > [!NOTE]
    > Эта строка подключения составлена из расчета того, что среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], сервер отчетов и база данных AdventureWorks2016 установлены на локальном компьютере.
    >
    >Если это не так, измените строку подключения, заменив loclahost именем своего сервера (экземпляра) базы данных. Если вы используете [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] или именованный экземпляр, включите в строку подключения сведения об этом экземпляре. Пример:
    >
    > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2016`
    >
    > Дополнительные сведения о строках подключения вы можете найти в разделе `See also` ниже.

6. Выберите вкладку **Учетные данные**, а затем в разделе **Change the credentials used to connect to the data source** (Изменить учетные данные, используемые для подключения к источнику данных) установите переключатель **Использовать проверку подлинности Windows (встроенная безопасность)**.

7. Чтобы завершить процесс, нажмите кнопку **ОК**.

Конструктор отчетов добавляет источник данных AdventureWorks2016 в панель **Данные отчета**.

![ssrs-adventureworks-datasource](media/lesson-2-specifying-connection-information-reporting-services/ssrs-adventureworks-datasource2016.png)

## <a name="next-steps"></a>Дальнейшие действия

В этом уроке вы успешно создали подключение к примеру базы данных AdventureWorks2016. Переходите к статье [Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md), где вы настроите набор данных для отчета.

## <a name="see-also"></a>См. также раздел

[Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)

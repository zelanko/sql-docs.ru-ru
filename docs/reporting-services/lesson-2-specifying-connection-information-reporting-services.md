---
title: Занятие 2. Задание информации о соединении (службы Reporting Services) | Документы Майкрософт
ms.date: 05/01/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0a0c21b2662fc14977c4ac57687754d15d544994
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65106060"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Занятие 2. Задание информации о соединении (службы Reporting Services)

В уроке 1 вы добавили отчет с разбиением на страницы [!INCLUDE[ssrsnoversion-md](../includes/ssrsnoversion-md.md)] к проекту Tutorial.
  
В этом уроке вы определите *источник данных*, то есть настроите сведения о подключении для доступа отчета к данным из реляционной базы данных или других источников.

Для этого отчета вы добавите в качестве источника данных пример базы данных AdventureWorks2016. В руководстве предполагается, что эта база данных находится в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] по умолчанию, установленном на локальном компьютере.  

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

## <a name="next-steps"></a>Следующие шаги

В этом уроке вы успешно создали подключение к примеру базы данных AdventureWorks2016. Теперь переходите к уроку 3 [Определение набора данных для табличного отчета (службы Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md), где вы определите набор данных для этого отчета.

## <a name="see-also"></a>См. также раздел

[Подключения данных, Источники данных и Строки подключения в службе Reporting Services](report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)

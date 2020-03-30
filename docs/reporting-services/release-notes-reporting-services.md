---
title: Заметки о выпуске SQL Server Reporting Services 2017 или более поздних версий | Документация Майкрософт
ms.date: 12/04/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maggies
author: casualoak
ms.author: rhys
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 39049ee5a2561821e0a2284ed66b9b04730998bf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74834251"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Заметки о выпуске SQL Server Reporting Services (SSRS) 2017 и более поздних версий

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

В этой статье описываются изменения в [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) для версий 2017 и более поздних.

Заметки о выпуске для элементов управления средства просмотра отчетов см. в [этой статье](application-integration/release-notes-ssrs-application-integration.md).

<!--
We are "standardizing" all our 'Release Notes' style articles:

  - File names:   'release-notes-[TechArea-Name].md'


  - Content format:   2-column tables.  No longer using bullet lists.

    - Ideally, the 'Details' column should contain a link to another SSRS documentation article wherein the particular issue fix is discussed in any way.  Or if there is more to say beyond one sentence, the other sentences of elaboration would go into the 'Details' column.


  - H2 header names are kept short, for better display.


  - Try to keep all Release Notes in one .md file.  Avoid having multiple R.N. files whose names differ only by version or date.

    - Seriously consider erasing info about ancient releases that are so old that nobody cares about them anymore.  If you really want to retain ancient info, consider doing so in an HTML comment at the end of the .md file, just in case a Microsoft employee needs to re-examine ancient info.  In any case, this file cannot get ever longer, and some deletion or hiding of oldest info must eventually occur.


  - Do use '::: moniker range=' zones when version 2017 is no longer the only version represented inside this .md file.

    - Use the '=' operator on the moniker, not the '>=' operator.
    - In contrast, in our 'Whats New' articles we do use the '>=', rather than '='.

GeneMi, DevOps = 1467988 (MsEng > TechnicalContent) , 2019/03/19
-->
## <a name="1406001451-20191113"></a>14.0.600.1451, 13.11.2019 

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Обновления для системы безопасности | &nbsp; |
| Отчеты с разбивкой на страницы не работали должным образом с параметрами фильтра при включенном моментальном снимке.  | &nbsp; |
| Пользователи с ролью "Обозреватель" и параметрами по умолчанию не имели разрешений на скачивание файлов Excel.  | &nbsp; |
| При переходе с SQL Server 2016 Reporting Services на Сервер отчетов Power BI происходил сбой. | &nbsp; |
| После перехода с SQL Server 2012 Reporting Services в подписках возникало сообщение об ошибке "Недопустимый знак в заголовке электронной почты". | &nbsp; |
| Средство настройки: отмена модальных окон в разделе базы данных приводила к перезапуску службы Reporting Services. | &nbsp; |
| Выражение свойства BorderStyle элементов управления "Текстовое поле" не преобразовывалось для просмотра в формат Excel.  | &nbsp; |
| Проблема разбиения на страницы, при которой некоторые отчеты могли зависнуть на отрисовке одной и той же страницы, так и не достигнув последней страницы отчета. | &nbsp; |

## <a name="1406001274-20190701"></a>14.0.600.1274, 01.07.2019

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Обновления для системы безопасности | &nbsp; |
| Не удается выбрать рабочие дни при создании общего расписания на неделю. | &nbsp; |
| В отчете неправильно отображаются символы возврата каретки в формате Word. | &nbsp; |
| System Center Operations Manager(SCOM) 2019 больше не работает с последними обновлениями SSRS 2017. | &nbsp; |
| При вызове расширения авторизации для общего набора данных происходила ошибка. | &nbsp; |
| В хранимой процедуре GetAllProperties в службах SSRS 2017 и PBIRS изменилась логика. Это приводило к тому, что метод ReportingService2010.GetProperties конечной точки веб-службы не мог получить данные для связанного отчета. | &nbsp; |
| Заголовок строки простой сетки исчезает при щелчке элемента сетки в мобильном отчете. | &nbsp; |
| Не удается использовать поле даты в параметре управляемой данными подписки. | &nbsp; |
| В службах SSRS 2016 и более поздних версий вложенный табликс отображает мелкий или частичный шрифт. | &nbsp; |
| Ошибка параметра DateTime в подписке после редактирования подписки пользователем, у которого другой языковой стандарт. | &nbsp; |
| Создание управляемой данными подписки с модулем доставки NULL завершается ошибкой "Произошла ошибка доставки". | &nbsp; |
| Неправильное кодирование URL-адреса, если задается значение в формате Excel или Word. | &nbsp; |

## <a name="1406001109-20190212"></a>14.0.600.1109, 12.02.2019

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Моментальный снимок отчета кэша будет использовать режим расписания отчета после изменения в подписку. | &nbsp; |
| Параметр rc:Toolbar=false не работает в экспресс-выпуске. | &nbsp; |
| При экспорте отчетов с разбиением на страницы в формат PDF определенные тайские символы отображаются неправильно. | &nbsp; |
| Взаимоблокировки во время отправки уведомления о завершении подписок, управляемых данными. | &nbsp; |
| Внедренные образы не отображаются в определенных случаях при использовании параметра rc:Toolbar=False. | &nbsp; |
| Не удалось создать управляемые данными подписки для отчетов, использующих каскадные параметры. | &nbsp; |
| Не удалось изменить подписки, настроенные с использованием недопустимых интервалов. | &nbsp; |
| Обновления для системы безопасности. | &nbsp; |
| Пользовательский интерфейс связанных отчетов не отображается. | &nbsp; |
| Некоторые отчеты с разбивкой на страницы с вложенными элементами управления табликса имеют неправильные шрифты. | &nbsp; |
| Пробелы неправильно добавляются в определенные отчеты с разбивкой на страницы, содержащие области данных табликса. | &nbsp; |
| Заголовок строки исчезает при расширении простых сеток данных в мобильных отчетах. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906, 12.09.2018

Исправлены следующие проблемы:

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Пользовательская аутентификация возвращает неправильные сведения о файлах cookie. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892, 31.08.2018

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Прямоугольник текстового поля не растягивается вертикально при наличии длинного текста и использовании параметра rc:Toolbar=False. | &nbsp; |
| Размер текста не масштабируется, если значение pageHeight менее 1,25 см. | &nbsp; |
| Взаимоблокировка в базе данных каталога SSRS при использовании с CRM. | &nbsp; |
| Заголовки столбцов, выровненные по вертикали, неправильно отображаются при прокрутке отчета. | &nbsp; |
| Пользователям, которым назначена роль оператора отчетов SCOM, заблокирован доступ к веб-порталу служб SSRS. | &nbsp; |
| Тайский символ экспортируется неправильно в формат PDF. | &nbsp; |
| Изменение поведения роли браузера. | &nbsp; |
| Параметр rc:Toolbar=false не работает в выпуске Express. | &nbsp; |
| Отсутствует вертикальная полоса прокрутки в области запроса параметров. | &nbsp; |
| Среда выполнения мобильного отчета обновлена. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744, 25.04.2018

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Страница управляемой данными подписки не содержит параметр доставки после создания. | &nbsp; |
| Обновление служб SSRS 2012 до версии SSRS 2017 приводит к возникновению исключения RSManagement каждые несколько секунд. | &nbsp; |
| Невозможно изменить значения по умолчанию для многозначных параметров в IE11. | &nbsp; |
| Расписания являются пустыми при каждом выполнении общего расписания. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689, 28.02.2018

| Исправленные проблемы | Сведения |
| :---------- | :------ |
| Отменены изменения видимости параметра отчета в связанном отчете после изменения его свойств. | &nbsp; |
| Параметр rc:Toolbar=false URL-адреса не работает в экспресс-выпуске. | &nbsp; |
| Если в выражениях в текстовом поле для свойства CanGrow задано значение false, значения не отображались. | &nbsp; |
| Добавлена ссылка _Дополнительные сведения_ для ключа продукта в программе установки. | &nbsp; |
| На веб-портале с проверкой подлинности на основе форм игнорируется файл cookie с возобновляемым сроком действия. | &nbsp; |
| При экспорте в Word строки без содержимого имеют разную высоту. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594, 09.01.2018

Реализованы некоторые обновления для системы безопасности.

### <a name="140600490-20171101"></a>14.0.600.490, 01.11.2017

Устранены проблемы с обновлением номера SKU.

## <a name="140600451-20170930"></a>14.0.600.451, 30.09.2017

Начальный выпуск.

## <a name="next-steps"></a>Дальнейшие действия

[Новые возможности служб Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

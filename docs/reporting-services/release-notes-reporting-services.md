---
title: Заметки о выпуске для (SSRS) 2017 и более поздних версий | Документация Майкрософт
ms.date: 02/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maggies
author: casualoak
ms.author: rhys
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: cd2f9dec39075b332b2ae38c622f3970faf8d331
ms.sourcegitcommit: c40f663d4486e574fd749f2c8e84c98d41970352
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67037852"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Заметки о выпуске SQL Server Reporting Services (SSRS) 2017 и более поздних версий

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

В этой статье описываются изменения в [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS), для 2017 и более поздних версиях.

Заметки о выпуске для элементов управления средства просмотра отчетов, см. в разделе [заметки о выпуске для средства просмотра отчетов, элементы управления для веб-форм и WinForms служб SSRS](application-integration/release-notes-ssrs-application-integration.md).

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

## <a name="1406001109-20190212"></a>14.0.600.1109, 12.02.2019

| Исправлена проблема | Сведения |
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
| Пробел добавляется неправильно для некоторых отчетов с разбиением на страницы, содержащие области данных табликса. | &nbsp; |
| Заголовок строки исчезает при расширении простых сеток данных в мобильных отчетах. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906, 12.09.2018

Исправлены следующие проблемы:

| Исправлена проблема | Сведения |
| :---------- | :------ |
| Пользовательская аутентификация возвращает неправильные сведения о файлах cookie. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892, 31.08.2018

| Исправлена проблема | Сведения |
| :---------- | :------ |
| Прямоугольник текстового поля не растягивается вертикально при наличии длинного текста и использовании параметра rc:Toolbar=False. | &nbsp; |
| Размер текста не масштабируется, если значение pageHeight менее 1,25 см. | &nbsp; |
| Взаимоблокировка возникает в базе данных каталога SSRS, когда используется в сочетании с CRM. | &nbsp; |
| Заголовки столбцов, выровненные по вертикали, неправильно отображаются при прокрутке отчета. | &nbsp; |
| Пользователи, добавленные в роль отчетов System Center Operations Manager имеют доступ к заблокирован SSRS веб-портал. | &nbsp; |
| Тайские символ не является корректно экспортированы в PDF-ФАЙЛ. | &nbsp; |
| Изменение поведения роли браузера. | &nbsp; |
| Параметр rc:Toolbar=false не работает в выпуске Express. | &nbsp; |
| Отсутствует вертикальную полосу прокрутки в область запроса параметров. | &nbsp; |
| Среда выполнения мобильного отчета обновлена. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744, 25.04.2018

| Исправлена проблема | Сведения |
| :---------- | :------ |
| Страница управляемой данными подписки не содержит параметр доставки после создания. | &nbsp; |
| Обновление служб SSRS 2012 до версии SSRS 2017 приводит к возникновению исключения RSManagement каждые несколько секунд. | &nbsp; |
| Невозможно изменить значения по умолчанию для многозначных параметров в IE11. | &nbsp; |
| Расписания являются пустыми при каждом выполнении общего расписания. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689, 28.02.2018

| Исправлена проблема | Сведения |
| :---------- | :------ |
| Отменены изменения видимости параметра отчета в связанном отчете после изменения его свойств. | &nbsp; |
| Параметр rc:Toolbar=false URL-адреса не работает в экспресс-выпуске. | &nbsp; |
| Если в выражениях в текстовое поле с CanGrow свойство, значение false приводит значения не отображаются. | &nbsp; |
| Добавлена ссылка _Дополнительные сведения_ для ключа продукта в программе установки. | &nbsp; |
| На веб-портале с проверкой подлинности на основе форм игнорируется файл cookie с возобновляемым сроком действия. | &nbsp; |
| При экспорте в Word строки без содержимого имеют разную высоту. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594, 09.01.2018

Некоторые обновления для системы безопасности были реализованы.

### <a name="140600490-20171101"></a>14.0.600.490, 01.11.2017

Устранены проблемы с обновлением номера SKU.

## <a name="140600451-20170930"></a>14.0.600.451, 30.09.2017

Начальный выпуск.

## <a name="next-steps"></a>Следующие шаги

[Новые возможности служб Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).

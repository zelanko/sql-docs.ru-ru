---
title: Импорт неструктурированных файлов в SQL | Документация Майкрософт
ms.custom: ''
ms.date: 09/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: data-movement
ms.topic: conceptual
f1_keywords:
- sql13.swb.importflatfile.f1
author: yualan
ms.author: alayu
ms.reviewer: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 962ed44bad714125f78cac5adff5af42b0c76685
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138441"
---
# <a name="import-flat-file-to-sql-wizard"></a>Мастер импорта неструктурированных файлов в SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
> Сведения о мастере импорта и экспорта см. в разделе [Мастер импорта и экспорта SQL Server](https://docs.microsoft.com/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard).

Мастер импорта неструктурированных файлов позволяет легко скопировать данные из неструктурированного файла (CSV-файл, TXT-файл) в новую таблицу в вашей базе данных. В этом обзоре описано, почему нужно использовать этот мастер, как его найти, а также приведен простой пример.

## <a name="why-would-i-use-this-wizard"></a>Почему нужно использовать этот мастер?
Этот мастер создан на основе интеллектуальной платформы Program Synthesis using Examples ([PROSE](https://microsoft.github.io/prose/)) и позволяет улучшить текущий процесс импорта. Для пользователей, которые не обладают глубокими знаниями в предметной области, импорт данных часто представляет собой трудную и утомительную задачу, чреватую ошибками. При использовании мастера достаточно указать входной файл и уникальное имя таблицы, и платформа PROSE сделает все остальное.

PROSE анализирует шаблоны данных во входном файле и определяет имена столбцов, типы, разделители и т. д. Платформа запоминает структуру файла и выполняет все действия по обработке данных.

Подробные сведения о том, как улучшен пользовательский интерфейс мастера импорта неструктурированных файлов, см. в этом видео.

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-new-Import-Flat-File-Wizard-in-SSMS-173/player]

## <a name="prerequisites"></a>предварительные требования
Эта функция доступна только в SQL Server Management Studio (SSMS) 17.3 и более поздних версиях. Убедитесь, что вы используете последнюю версию. Ее можно найти [здесь](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
 
## <a id="started"></a> Приступая к работе
Чтобы открыть мастер импорта неструктурированных файлов, выполните следующие действия.

1. Откройте **SQL Server Management Studio**.
2. Подключитесь к экземпляру ядра СУБД SQL Server или к узлу localhost.
3. Разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных ("test" в примере ниже), выберите **Задачи**, а затем — **Импорт неструктурированного файла** над пунктом меню "Импорт данных".

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

![Меню мастера](media/import-flat-file-wizard/importffmenu.png)

Дополнительные сведения о различных функциях мастера см. в следующем руководстве:

## <a name="tutorial"></a>Учебник
При выполнении действий, описанных в этом учебнике, вы можете использовать свой собственный неструктурированный файл. Если у вас нет собственного файла, можете скопировать следующий CSV-файл из Excel. Назовите этот файл **example.csv** и сохраните его в формате CSV в удобном месте, например на рабочем столе.

![Пример файла Excel для проверки мастера](media/import-flat-file-wizard/importffexample.png)

### <a name="step-1-access-wizard-and-intro-page"></a>Шаг 1. Открытие мастера и страница "Приступая к работе"
Откройте мастер, как описано [здесь](#started).

Первая страница мастера — это страница приветствия. Если вы не хотите, чтобы она открывалась снова, установите флажок **Больше не показывать это окно**.

![Страница "Приступая к работе"](media/import-flat-file-wizard/importffintro.png)

### <a name="step-2-specify-input-file"></a>Шаг 2. Указание входного файла
Нажмите кнопку "Обзор", чтобы выбрать входной файл. По умолчанию мастер ищет файлы в форматах CSV и TXT. 

Имя новой таблицы должно быть уникальным. В противном случае вы не сможете продолжить работу мастера.

![Страница "Указание входного файла"](media/import-flat-file-wizard/importffspecify.png)

### <a name="step-3-preview-data"></a>Шаг 3. Просмотр данных
Мастер открывает окно предварительного просмотра для первых 50 строк данных. Если в данных есть ошибки, нажмите кнопку "Отмена". В противном случае перейдите к следующей странице.

![Страница "Предварительный просмотр данных"](media/import-flat-file-wizard/importffpreview.png)

### <a name="step-4-modify-columns"></a>Шаг 4. Изменение столбцов
Мастер определяет имена столбцов, типы данных и т. д. Здесь можно изменить поля, если они определены неверно (например, указать тип данных с плавающей точкой вместо целочисленного типа).

Когда все будет готово, нажмите кнопку "Далее".

![Страница "Изменение столбцов"](media/import-flat-file-wizard/importffmodify.png)

### <a name="step-5-summary"></a>Шаг 5. Сводка
Это страница сводки, на которой отображается текущая конфигурация. Если возникли проблемы, можно вернуться к предыдущим страницам мастера. В противном случае нажмите кнопку "Готово", чтобы начать импорт.

![Страница "Сводка"](media/import-flat-file-wizard/importffsummary.png)

### <a name="step-6-results"></a>Шаг 6. Результаты
На этой странице показан результат импорта. Если на ней есть зеленая галочка, импорт завершен успешно. В противном случае проверьте конфигурацию и входной файл на наличие ошибок.

![Страница "Результаты"](media/import-flat-file-wizard/importffresults.png)

## <a name="learn-more"></a>Дополнительные сведения

Дополнительные сведения о мастере.
 
- **Дополнительные сведения об импорте из других источников**. Если вы хотите импортировать несколько неструктурированных файлов, обратитесь к разделу [Мастер импорта и экспорта SQL Server](https://docs.microsoft.com/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard).
- **Дополнительные сведения о подключении к неструктурированным файлам в качестве источников**. Если вам необходимы дополнительные сведения о подключении к неструктурированным файлам в качестве источников, обратитесь к разделу [Подключение к источнику данных неструктурированного файла](https://docs.microsoft.com/sql/integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard).
- **Дополнительные сведения о PROSE**. Если вам необходимы сведения об интеллектуальной платформе, которая используется этим мастером, обратитесь к разделу [Пакет SDK для PROSE](https://microsoft.github.io/prose/).


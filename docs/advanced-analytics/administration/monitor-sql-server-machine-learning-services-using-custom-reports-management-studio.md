---
title: Мониторинг выполнения скриптов Python и R с помощью пользовательских отчетов в среде SSMS
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 549cdcd35b939b2247b14817271e3d1063fab1e0
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714398"
---
# <a name="monitor-python-and-r-script-execution-using-custom-reports-in-sql-server-management-studio"></a>Мониторинг выполнения скриптов Python и R с помощью пользовательских отчетов в SQL Server Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Используйте пользовательские отчеты в SQL Server Management Studio (SSMS) для наблюдения за выполнением внешних скриптов (Python и R), используемых ресурсов, диагностики проблем и настройки производительности в SQL Server Службы машинного обучения.

В этих отчетах можно просмотреть следующие сведения:

- Активные сеансы Python или R
- Параметры конфигурации для экземпляра
- Статистика выполнения заданий машинного обучения
- Расширенные события для служб R
- Пакеты Python или R, установленные на текущем экземпляре

В этой статье объясняется, как установить и использовать настраиваемые отчеты, предоставленные для SQL Server Службы машинного обучения.

Дополнительные сведения об отчетах в SQL Server Management Studio см. [в разделе Пользовательские отчеты в Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>Установка отчетов

Отчеты разрабатываются с помощью SQL Server Reporting Services, но их можно использовать непосредственно из SQL Server Management Studio. Reporting Services не обязательно устанавливать на экземпляре SQL Server.

Чтобы использовать эти отчеты, выполните следующие действия.

1. Скачайте [пользовательские отчеты SSMS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports) для SQL Server службы машинного обучения с сайта GitHub.

2. Копирование отчетов в Management Studio

    1. Найдите папку настраиваемых отчетов, используемую SQL Server Management Studio. По умолчанию пользовательские отчеты хранятся в этой папке (где **user_name** — имя пользователя Windows):

        `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

       Можно также указать другую папку или создать вложенные папки.

    2. Скопируйте *. RDL-файлы, скачанные в папку пользовательских отчетов.

3. Запуск отчетов в Management Studio

    1. В Management Studio щелкните правой кнопкой мыши узел **Базы данных** для экземпляра, на котором вы хотите запустить отчеты.

    2. Щелкните **Отчеты**, а затем **Настраиваемые отчеты**.

    3. В диалоговом окне **Открыть файл** найдите папку настраиваемых отчетов.

    4. Выберите один из загруженных ранее RDL-файлов и нажмите кнопку **Открыть**.

## <a name="reports"></a>Отчеты

[Репозиторий пользовательских отчетов SSMS в GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports) содержит следующие отчеты:

| Отчет | Описание |
|-|-|
| Активные сеансы | Пользователи, которые в настоящее время подключены к экземпляру SQL Server и запускают скрипты Python или R. |
| Конфигурация | Параметры установки Службы машинного обучения и свойств среды выполнения Python или R. |
| Настройка экземпляра | Настройте Службы машинного обучения. |
| Статистика выполнения | Статистика выполнения служб Машинное обучение. Например, можно получить общее число выполнений внешних скриптов и количество параллельных выполнений. |
| Расширенные события | Расширенные события, доступные для получения дополнительных сведений о выполнении внешних скриптов. |
| Пакеты | Список пакетов R или Python, установленных на экземпляре SQL Server, и их свойства, такие как версия и имя. |
| Использование ресурсов | Просмотр использования ЦП, памяти, операций ввода-вывода в SQL Server и выполнения внешних скриптов. Кроме того, можно просмотреть параметры памяти для внешних пулов ресурсов. |

## <a name="next-steps"></a>Следующие шаги

- [Мониторинг SQL Server Службы машинного обучения с помощью динамических административных представлений](monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
- [Расширенные события для служб R](../r/extended-events-for-sql-server-r-services.md)

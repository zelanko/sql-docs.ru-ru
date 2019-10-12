---
title: Руководство для специалистов по обработке и анализу данных с использованием языка R
description: Учебник, показывающий, как создать комплексное решение R для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/11/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad7f5a500f740e4a302f814ec9523dfb33ecc68b
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278276"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Учебник. Разработка SQL для специалистов по анализу данных R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом учебнике для специалистов по обработке и анализу данных Узнайте, как создать комплексное решение для прогнозного моделирования на основе поддержки функций R в SQL Server 2016 или SQL Server 2017. В этом руководстве используется база данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) на SQL Server. 

Вы используете сочетание кода R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользовательских функций SQL для построения модели классификации, которая указывает вероятность того, что драйвер может получить совет по определенному пути такси. Вы также развертываете модель R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и используете данные сервера для создания оценок на основе модели.

Этот пример можно расширить на все виды реальных проблем, таких как прогнозирование ответов клиентов на кампании по продажам или прогнозирование расходов или посещаемости на мероприятиях. Поскольку модель может быть вызвана из хранимой процедуры, ее можно легко внедрить в приложение.

Так как это пошаговое руководство предназначено для разработчиков R, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R используется везде, где это возможно. Однако это не означает, что R является необязательно лучшим средством для каждой задачи. Во многих случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обеспечивать более высокую производительность, особенно для таких задач, как агрегирование данных и формирование характеристик.  Для выполнения таких задач новые возможности [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], такие как оптимизированные для памяти индексы columnstore, могут быть особенно полезны. Мы пытаемся указать возможные способы оптимизации.

## <a name="prerequisites"></a>Предварительные требования

+ [SQL Server службы машинного обучения с интеграцией r](../install/sql-machine-learning-services-windows-install.md#verify-installation) или [службами SQL Server 2016 r](../install/sql-r-services-windows-install.md)

+ [Разрешения базы данных](../security/user-permission.md) и имя входа пользователя базы данных SQL Server

+ [Среда SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Демонстрационная база данных такси Нью](demo-data-nyctaxi-in-sql.md)

+ Интегрированная среда разработки R, например RStudio или встроенное средство RGUI, входящее в R

Мы рекомендуем выполнить это пошаговое руководство на клиентской рабочей станции. Необходимо иметь возможность подключения к той же сети, к компьютеру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с SQL Server и включенным языком R. Инструкции по настройке рабочей станции см. в разделе [Настройка клиента обработки и анализа данных для разработки на R](../r/set-up-a-data-science-client.md).

Кроме того, можно выполнить пошаговое руководство на компьютере, где есть как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и среду разработки R, но мы не рекомендуем использовать эту конфигурацию для рабочей среды. Если необходимо разместить клиент и сервер на одном компьютере, установите второй набор библиотек Microsoft R для отправки сценария R с удаленного клиента. Не используйте библиотеки R, установленные в программных файлах экземпляра SQL Server. В частности, если используется один компьютер, то для поддержки операций клиента и сервера необходима библиотека RevoScaleR в обоих расположениях.

+ C:\Program Филес\микрософт\р Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

> [!NOTE]
> Если вы используете [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/) или [виртуальную машину](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/)для обработки и анализа данных, а не R Client, путь к RevoScaleR будет C:\Program филес\микрософт\мл Server\R_SERVER\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Дополнительные пакеты R

В этом пошаговом руководстве требуется несколько библиотек R, которые не устанавливаются по умолчанию в составе [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Пакеты необходимо установить как на клиенте, где разрабатывается решение, так и на компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором развертывается решение.

### <a name="on-a-client-workstation"></a>На клиентской рабочей станции

В среде R скопируйте следующие строки и выполните код в окне консоли (RGUI или в интегрированной среде разработки). Некоторые пакеты также устанавливают необходимые пакеты. В любом случае устанавливаются сведения о пакетах 32. Для выполнения этого шага необходимо подключение к Интернету.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>На сервере

Существует несколько вариантов установки пакетов на SQL Server. Например, SQL Server предоставляет функцию [управления пакетами R](../r/install-additional-r-packages-on-sql-server.md) , которая позволяет администраторам баз данных создавать репозиторий пакетов и назначать пользователю права на установку собственных пакетов. Однако если вы являетесь администратором на компьютере, то можете установить новые пакеты с помощью R при условии, что установка выполняется в нужную библиотеку.

> [!NOTE]
> На сервере **не устанавливайте** в библиотеку пользователей, даже если появится соответствующий запрос. При установке в пользовательской библиотеке экземпляр SQL Server не сможет найти или запустить пакеты. Дополнительные сведения см. [в разделе Установка новых пакетов R на SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. На компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откройте программу RGui.exe **от имени администратора**.  Если вы установили SQL Server R Services, используя значения по умолчанию, RGUI. exe можно найти в папке C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).

2. В командной строке R выполните следующие команды R:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  В этом примере функция R grep используется для поиска вектора доступных путей и поиска пути, включающего "Program Files". Дополнительные сведения см. в разделе [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep).

  Если вы считаете, что пакеты уже установлены, проверьте список установленных пакетов, выполнив `installed.packages()`.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Просмотр и сведение данных](walkthrough-view-and-summarize-data-using-r.md)

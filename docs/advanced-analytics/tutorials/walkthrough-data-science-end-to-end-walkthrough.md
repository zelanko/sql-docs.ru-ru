---
title: Учебник по R. Разработка модели в SQL
description: Учебник, показывающий, как создать комплексное решение R для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/11/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9844746d6887c14e5524ed54c39e2de7e0375eb1
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73723799"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Руководство. SQL-разработка на языке R для специалистов по анализу данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом учебнике для специалистов по обработке и анализу данных рассказывается, как создать комплексное решение для прогнозного моделирования на основе поддержки функций R в SQL Server 2016 и SQL Server 2017. В этом учебнике используется база данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) на SQL Server. 

Используя сочетание кода на языке R, данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользовательских функций SQL, вы создадите модель классификации, которая сообщает вероятность получения чаевых таксистом за конкретную поездку. Вы также развернете модель R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и воспользуетесь данными на сервере для формирования оценок на основе модели.

Этот пример можно адаптировать для решения других реальных проблем, таких как прогнозирование отклика клиентов на кампании по сбыту или прогнозирование выручки или посещаемости на мероприятии. Так как модель можно вызывать из хранимой процедуры, ее можно легко внедрить в приложение.

Поскольку это пошаговое руководство призвано познакомить разработчиков на языке R со службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], то во всех возможных случаях используется язык R. Однако, это не означает, что он является лучшим средством для выполнения каждой задачи. Во многих случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обеспечивать более высокую производительность, особенно для таких задач, как агрегирование данных и формирование характеристик.  Для выполнения таких задач новые возможности [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], такие как оптимизированные для памяти индексы columnstore, могут быть особенно полезны. Кроме того, мы попытаемся указать возможные пути оптимизации.

## <a name="prerequisites"></a>предварительные требования

+ [Службы машинного обучения SQL Server с интеграцией языка R](../install/sql-machine-learning-services-windows-install.md#verify-installation) или [Службы SQL Server 2016 R](../install/sql-r-services-windows-install.md)

+ [Разрешения для базы данных](../security/user-permission.md) и имя пользователя для входа в базу данных SQL Server

+ [Среда SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Демонстрационная база данных такси Нью-Йорка](demo-data-nyctaxi-in-sql.md)

+ Интегрированная среда разработки R, например RStudio или средство RGUI, входящее в состав R

Мы рекомендуем выполнять это пошаговое руководство на клиентской рабочей станции. Необходимо иметь возможность подключения к находящемуся в той же сети компьютеру с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и включенным языком R. Инструкции по настройке рабочей станции см. в разделе [Настройка клиента обработки и анализа данных для разработки на R](../r/set-up-a-data-science-client.md).

Вы также можете выполнить это пошаговое руководство на компьютере, где установлены как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и среда разработки R, но мы не рекомендуем использовать такую конфигурацию в рабочей среде. Если необходимо разместить клиент и сервер на одном компьютере, установите второй набор библиотек Microsoft R, чтобы отправлять сценарий R из "удаленного" клиента. Не используйте библиотеки R, установленные в программных файлах экземпляра SQL Server. В частности, если используется один компьютер, то для поддержки операций клиента и сервера необходимо иметь библиотеку RevoScaleR в обоих расположениях.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

> [!NOTE]
> Если вы используете [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/) или [Виртуальную машину для обработки и анализа данных](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/), RevoScaleR должна располагаться не в папке клиента R, а в папке C:\Program Files\Microsoft\ML Server\R_SERVER\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Дополнительные пакеты R

Для работы с этим пошаговым руководством требуется ряд библиотек R, которые по умолчанию не устанавливаются вместе с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Эти пакеты необходимо установить как на клиентском компьютере, на котором разрабатывается решение, так и на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где оно будет развертываться.

### <a name="on-a-client-workstation"></a>На клиентской рабочей станции

В среде R скопируйте следующие строки и выполните код в окне консоли (RGUI или в интегрированной среде разработки). Необходимые пакеты также будут установлены. Всего будет установлено около 32 пакетов. Для выполнения этого этапа необходимо подключение к Интернету.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>На сервере

Существует несколько вариантов установки пакетов на SQL Server. Например, SQL Server предоставляет функцию [Управление пакетами R](../r/install-additional-r-packages-on-sql-server.md), которая позволяет администраторам баз данных создавать репозиторий пакетов и назначать пользователю права на установку собственных пакетов. Однако если вы являетесь администратором на компьютере, то вы можете установить новые пакеты с помощью R при условии, что установка выполняется в нужную библиотеку.

> [!NOTE]
> На сервере **не нужно** устанавливать в пользовательскую библиотеку, даже если появляется соответствующий запрос. При установке в пользовательскую библиотеку экземпляр SQL Server не сможет найти и запустить пакеты. Дополнительные сведения см. в статье [Установка новых пакетов R в SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. На компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откройте программу RGui.exe **от имени администратора**.  Если вы установили службы R SQL Server с настройками по умолчанию, программу Rgui.exe можно найти в папке C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64.

2. В командной строке R выполните следующие команды R:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  В этом примере используется функция R grep для поиска вектора доступных путей, которая находит путь, содержащий "Program Files". Дополнительные сведения см. в статье [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep).

  Если вы считаете, что пакеты уже установлены, проверьте список установленных пакетов, выполнив команду `installed.packages()`.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Просмотр и обобщение данных](walkthrough-view-and-summarize-data-using-r.md)

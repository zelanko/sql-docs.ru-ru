---
title: Руководство по обработке и анализу данных с помощью языка R - машинного обучения SQL Server
description: Учебник, в котором показано, как создать решение R end-to-end для аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7fbed76272903fb7a9b6eee037a070677411a0f5
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596425"
---
# <a name="tutorial-in-database-analytics-for-data-scientists-using-r"></a>Учебник. Аналитика в базе данных для специалистов по анализу данных с помощью языка R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом учебнике по обработке и анализу данных сведения о создании решений end-to-end для прогнозирующего моделирования, в зависимости о поддержке компонентов R в SQL Server 2016 или SQL Server 2017. В этом руководстве используется [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) базы данных на сервере SQL Server. 

Использовать сочетание кода R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных и пользовательских функций SQL для построения модели классификации, обозначающее вероятность, что драйвер может получения чаевых таксистом за конкретную поездку. Вы также развернуть модель R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать данные сервера для формирования оценок на основе модели.

В этом примере можно расширить решения других реальных проблем, таких как прогнозирование отклика клиентов на кампании по сбыту или прогнозирование расходов или отсутствие события. Так как модель можно вызывать из хранимой процедуры, можно легко внедрить в приложение.

Так как данное пошаговое руководство предназначено для ознакомления разработчиков R для [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R используется в том случае, когда это возможно. Тем не менее это не означает, что язык R непременно является лучшим средством для каждой задачи. Во многих случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обеспечивать более высокую производительность, особенно для таких задач, как агрегирование данных и формирование характеристик.  Для выполнения таких задач новые возможности [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], такие как оптимизированные для памяти индексы columnstore, могут быть особенно полезны. Мы стараемся возможные оптимизации попутно.

## <a name="prerequisites"></a>предварительные требования

+ [Служб SQL Server 2017 машинного обучения с помощью интеграции R](../install/sql-machine-learning-services-windows-install.md#verify-installation) или [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [Разрешения базы данных](../security/user-permission.md) и имя входа пользователя базы данных SQL Server

+ [Среда SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Демонстрационная база данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)

+ R IDE, например RStudio или встроенное средство RGUI состав R

Мы рекомендуем выполнить в этом пошаговом руководстве на клиентской рабочей станции. Должен появиться возможность подключения, в той же сети, к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера с SQL Server и поддержкой языка R. Инструкции по конфигурации рабочей станции, см. в разделе [Настройка клиента обработки и анализа данных для средств разработки R](../r/set-up-a-data-science-client.md).

Кроме того, вы может работать с пошаговым руководством на компьютере, в котором содержатся оба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и среду разработки R, но мы не рекомендуем этой конфигурации для рабочей среды. Если вам нужно поместить клиента и сервера на одном компьютере, не забудьте установить второй набор библиотек Microsoft R для отправки скрипта R из «клиента». Не используйте библиотеки R, установленных в программные файлы экземпляра SQL Server. В частности Если вы используете один компьютер, необходимо библиотеки RevoScaleR в оба эти места для поддержки клиентских и серверных операций.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Дополнительные пакеты R

В этом пошаговом руководстве требуется несколько библиотек R, которые не устанавливаются по умолчанию как часть [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Необходимо установить пакеты как на стороне клиента, которой разработки решения, а также на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютере, где будут развернуты решения.

### <a name="on-a-client-workstation"></a>На клиентской рабочей станции

В среде R скопируйте следующие строки и выполните код в окне консоли (Rgui или интегрированная среда разработки). Некоторые пакеты также установить необходимые пакеты. В общем устанавливаются около 32 пакетов. Необходимо иметь подключение к Интернету для выполнения этого шага.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>На сервере

У вас есть несколько вариантов для установки пакетов на сервере SQL Server. Например, SQL Server предоставляет [управление пакетами R](../r/install-additional-r-packages-on-sql-server.md) компонент, который позволяет администраторам баз данных создание репозитория пакетов и назначить пользователю права на установку собственных пакетов. Тем не менее если вы являетесь администратором на компьютере, можно установить новые пакеты, с помощью языка R, до тех пор, пока установки в правильную библиотеку.

> [!NOTE]
> На сервере **не** установить библиотеку пользователя, даже при появлении соответствующего запроса. При установке в пользовательской библиотеке, экземпляр SQL Server не удается найти или запуске пакетов. Дополнительные сведения см. в разделе [Установка новых пакетов R в SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. На компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откройте программу RGui.exe **от имени администратора**.  Если вы установили службы R SQL Server, используя параметры по умолчанию, Rgui.exe можно найти в C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).

2. В командной строке R выполните следующие команды R:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  В этом примере используется функция R grep для поиска вектора доступных путей и нахождения пути, включающего «Program Files». Дополнительные сведения см. в разделе [ https://www.rdocumentation.org/packages/base/functions/grep ](https://www.rdocumentation.org/packages/base/functions/grep).

  Если вы считаете, что пакеты уже установлены, проверьте список установленных пакетов, выполнив `installed.packages()`.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Изучение и обобщения данных](walkthrough-view-and-summarize-data-using-r.md)
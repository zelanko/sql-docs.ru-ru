---
title: Подробное руководство - машинного обучения SQL Server функцию RevoScaleR
description: В этом учебнике вы научитесь вызывать функции RevoScaleR, используя интеграцию R для машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 48d65bfe54890c5ea0d8bfdca9c76fa0978a917d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641304"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Учебник. Использовать функции RevoScaleR R с данными SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) пакета Microsoft R, предоставляющего, распределенных и параллельной обработки для обработки и анализа данных и машинного обучения рабочих нагрузок. Для разработки R в SQL Server **RevoScaleR** является одним из основных встроенных пакетов, с помощью функции для создания объектов источника данных, задание контекста вычислений, управление пакетами и самое главное: работа с данными end-to-end, из импорта для визуализации и анализа. Алгоритмы машинного обучения в SQL Server с зависимостями от **RevoScaleR** источников данных. Учитывая важность **RevoScaleR**, узнать, когда и как вызвать ее функций является важным навыком. 

В этом руководстве нескольких частей представлена диапазон **RevoScaleR** функции для задач, связанных с анализом данных. В процессе вы узнаете, как создать контекст удаленных вычислений, перемещать данные между контекстами локальных и удаленных вычислений и выполнять код R на удаленном экземпляре SQL Server. Вы также узнаете, как анализировать и отображать данные как локально, так и на удаленном сервере, а также как создавать и развертывать модели.

## <a name="prerequisites"></a>предварительные требования

+ [Службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md) с помощью функции R, или [SQL Server 2016 R Services (в базе данных)](../install/sql-r-services-windows-install.md)
  
+ [Разрешения базы данных](../security/user-permission.md) и имя входа пользователя базы данных SQL Server

+ [Среда SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Например, RStudio или встроенное средство RGUI состав R IDE

Чтобы переключаться между контекстами локальных и удаленных вычислений, вам потребуется две системы. Локальным обычно называется рабочей станции разработки с недостаточно заряда аккумулятора для рабочих нагрузок обработки и анализа данных. Удаленный в этом случае SQL Server 2017 или SQL Server 2016 с включенной функцией R. 

Переключение контекстов вычисления является основан на той же версии **RevoScaleR** на локальных и удаленных системах. На локальной рабочей станции, вы можете получить **RevoScaleR** пакетов и связанных поставщиков, установив Microsoft R Client.

Если вам нужно поместить клиента и сервера на одном компьютере, не забудьте установить второй набор библиотек Microsoft R для отправки скрипта R из «клиента». Не используйте библиотеки R, установленных в программные файлы экземпляра SQL Server. В частности, если вы используете один компьютер, необходимо **RevoScaleR** библиотеки в обоих этих расположений для поддержки клиентских и серверных операций.

+ C:\Program Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

Инструкции по настройке клиента, см. в разделе [Настройка клиента обработки и анализа данных для средств разработки R](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>Средства разработки R

Обычно разработчикам R использовать интегрированные среды разработки для написания и отладки кода на языке R. Вот несколько советов:

- **Инструменты R для Visual Studio** (RTVS) — это бесплатный подключаемый модуль, который предоставляет Intellisense, отладку и поддержку Microsoft R. Его можно использовать с R Server и службы машинного обучения SQL Server. Чтобы скачать эти средства, перейдите на страницу [Средства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **RStudio** — одна из наиболее популярных сред для разработки на языке R. Дополнительные сведения см. в разделе [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Базовые средства R (R.exe, RTerm.exe, RScripts.exe) также устанавливаются по умолчанию при установке R в SQL Server или R Client. Если вы не хотите устанавливать интегрированную среду разработки, можно использовать встроенные средства R для выполнения кода в этом руководстве.

Помните, что **RevoScaleR** необходим на локальных и удаленных компьютерах. Не удается завершить этот учебник, с помощью универсальной установки RStudio или другой среды, в котором отсутствует библиотеки Microsoft R. Дополнительные сведения см. в разделе [Настройка клиента обработки и анализа данных](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Сводка задач

+ Данные изначально получаются из CSV- или XDF-файлов. Импортировать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функций в **RevoScaleR** пакета.
+ Обучение и оценка модели выполняется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] контекста вычислений. 
+ Используйте **RevoScaleR** функции для создания новых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы для сохранения результатов оценки.
+ Создание графиков обоих на сервере и в локальном контексте вычислений.
+ Обучить модель на основе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, выполнении кода R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.
+ Извлечение подмножества данных и сохраните его как файл XDF для повторного использования при анализе на локальной рабочей станции.
+ Получить новые данные для оценки, откройте подключение ODBC к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Оценка выполняется на локальной рабочей станции.
+ Создайте пользовательскую функцию R и запустите его на сервере контекста вычислений для выполнения моделирования.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Занятие 1. Создание базы данных и разрешения](deepdive-work-with-sql-server-data-using-r.md)
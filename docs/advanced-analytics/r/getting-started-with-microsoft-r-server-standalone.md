---
title: "Приступая к работе с изолированным сервером Microsoft R Server | Документация Майкрософт"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 5ff9e6bc9b6cebb4602683180737aa78e7deb6e3
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-machine-learning-server-standalone"></a>Приступая к работе с машины обучения Server (изолированный)
 
В SQL Server 2016 Microsoft R Server (изолированный) помогли приведения популярных R с открытым кодом языка в предприятии, чтобы включить высокопроизводительные аналитические решения, а также интеграцию с другими бизнес-приложениями.  

На 2017 г. SQL Server имя было изменено на машине обучения Server (изолированный) в соответствии с добавлением поддержки для языка Python. Обе версии доступны бесплатно для пользователей Enterprise Edition или Software Assurance.

В этой статье Общие сведения об использовании сервера обучения машины (или сервера R) и приступить к работе с установкой и образцы.

## <a name="why-use-a-standalone-server-for-machine-learning"></a>Зачем использовать отдельный сервер для машинного обучения

Если не нужно интегрировать машинного обучения решений с данными SQL Server, машины обучения Server предоставляет такую же поддержку распределенные и масштабируемые R и Python и более позволяет развертывание решений в Spark, Linux или Hadoop.

Сервер обучения машины также включает предварительно обученной модели для анализа изображения и анализ мнений, который можно сразу же использовать в приложениях.

Возможности ввода в эксплуатацию машины обучения Server поддерживает развертывания и распространения решений R и Python с помощью веб-служб с удаленного выполнения кластерных топологии для Spark и Hadoop MapReduce и поддержку для Windows или Linux.

**SQL Server 2016**

+ Установка Microsoft R Server (изолированный) из программы установки SQL Server 2016.

    Создание изолированного сервера, который полностью независим от служб R (в базе данных). Эта версия поддерживает только R. Настройка изолированного сервера включен в политике поддержки SQL Server Enterprise Edition. Дополнительные сведения см. в разделе [Создание изолированного сервера R Server](../../advanced-analytics/r/create-a-standalone-r-server.md).

+ Установка сервера R, с помощью отдельного установщика Windows.

    Этот установщик создает новый экземпляр Microsoft R Server, использующего политика поддержки жизненного цикла современного программного обеспечения Microsoft. Можно также установить R Server для Linux, Cloudera, Teradata и Hadoop.
    
    Дополнительные сведения см. в разделе [установить 9.1 R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

**SQL Server 2017**

+ Установите сервер обучения машины (изолированный) из программы установки 2017 г. SQL Server. 

    Этот параметр создает изолированный сервер для поддержки ввода в эксплуатацию машинного обучения в R и Python. Настройка изолированного сервера включен в политике поддержки SQL Server Enterprise Edition. Дополнительные сведения см. в разделе [Создание изолированного сервера R Server](../../advanced-analytics/r/create-a-standalone-r-server.md).  

+ Используйте новый автономный установщик Windows.

    Этот метод установки создает новый экземпляр сервера обучения компьютера, использующего политика поддержки жизненного цикла современного программного обеспечения Microsoft. Также можно установить сервер обучения машины Hadoop, Spark или Linux без дополнительной платы.
    
    Дополнительные сведения см. в разделе [Установка машины обучения сервера для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

**Обновление существующего сервера**

+ Если имеется существующий сервер или экземпляр, который нужно обновить, загрузите и запустите установщик на основе Windows для получения обновлений. 

    Дополнительные сведения см. в разделе [с помощью SqlBindR, чтобы обновить экземпляр](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="start-using-machine-learning-server"></a>Приступить к использованию сервера Machine обучения

 После настройки компонентов сервера и настройки IDE, что позволяет использовать двоичные файлы сервера обучения машины можно приступать к разработке решения с помощью новых API, например RevoScaleR и revoscalepy, MicrosoftML и olapR.
    
Чтобы приступить к работе, см. Эти руководства:

+ [Шаблоны решений](https://docs.microsoft.com/machine-learning-server/r/sample-solutions)

    Эти примеры служат для решений, которые демонстрируют, как применить машинного обучения в различных отраслях. Текущий сценарии находятся в розничной торговли, Финансы, здравоохранение и маркетинга.

+ [Изучите R и ScaleR в 25 функции](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): изучение этой коллекции распространяемый аналитические функции, которые обеспечивают высокий уровень производительности и масштабируемости для решения R. Она содержит параллелизуемые версии многих популярных пакетов моделирования для R, например кластеризацию методом К-средних, деревья и леса принятия решений, а также средства для работы с данными.

- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx)

    Пакет MicrosoftML — это набор обучения алгоритмов и преобразования, разрабатываемых в Майкрософт, быстрых и масштабируемых новой машины. Его можно использовать в R или Python. Дополнительные сведения см. в разделе [MicrosoftML для Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) и [MicrosoftML для R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).

## <a name="see-also"></a>См. также раздел

[Приступая к работе с SQL Server машинного самообучения, службы](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
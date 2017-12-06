---
title: "RevoScaleR | Документы Microsoft"
ms.custom: 
ms.prod: sql-non-specified
ms.date: 11/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 4e6f6994499132c9b61a5e3b63ebe680bedb4fa3
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="revoscaler"></a>RevoScaleR

RevoScaleR — это пакет машины обучения функций, предоставляемых корпорацией Майкрософт, которая поддерживает обработки и анализа данных в масштабе.

+ Функции поддерживают импорт данных, преобразования данных, формирования сводных данных, визуализации и анализа.

+ _В масштабе_ означает, что операции можно выполняются для очень больших наборов данных, в параллельном режиме и на распределенных файловых систем. Алгоритмы работают над наборами данных, которые не помещаются в памяти, с помощью фрагментации и дизассемблировать результатов после выполнения операции.

+ RevoScaleR обеспечивает множество улучшений функций R с открытым кодом. Существует соответствующий базовый наиболее популярных функций R функции RevoScaleR. Функции RevoScaleR, обозначаются знаком **rx** или **Rx** префикс, чтобы облегчить их идентификацию.

+ RevoScaleR служит в качестве платформы для обработки и анализа данных. Например, можно использовать контексты вычислений RevoScaleR и преобразования с алгоритмами состояние рисунка в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). Можно также использовать [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) для выполнения базовых функций R в параллельном режиме.

Примеры RevoScaleR в действии см. в этих блогах: 

+ [Построение и развертывание прогнозную модель с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Один миллион прогнозы с машины обучения сервера в секунду](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Прогнозирование с помощью MicrosoftML советы такси](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Оптимизация производительности с rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

## <a name="how-to-get-revoscaler"></a>Как получить RevoScaleR

Пакет RevoScaleR для R установлен бесплатно в клиенте Microsoft R. Если вы машины обучения Server или с помощью R в SQL Server, RevoScaleR включается по умолчанию.

При использовании Python, [revoscalepy](../python/what-is-revoscalepy.md) пакет предоставляет аналогичную функциональность.

> [!IMPORTANT]
> Нельзя загрузить или использовать независимо от продуктов и служб, предоставляющих такую пакета RevoScaleR.

## <a name="use-revoscaler-in-sql-server"></a>Использование RevoScaleR в SQL Server

Эти учебники и примеры демонстрируют, как использовать функции RevoScaleR для получения данных из SQL Server, построения моделей и сохранения моделей в базе данных для оценки.

+ [Узнайте, как использовать контексты вычислений](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков SQL: обучение и ввода в эксплуатацию модели](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Образцы продуктов корпорации Майкрософт в GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)

## <a name="learn-more-about-revoscaler"></a>Дополнительные сведения о RevoScaleR

Эти учебники демонстрируют использование RevoScaleR в других контекстах вычислений, поддерживаемых [машины обучения Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), включая Hadoop.

+ [Что такое RevoScaleR?](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)

+ [Просмотр в 25 функции RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)

+ [Ссылки на пакет RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)


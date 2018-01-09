---
title: "Изучение служб машины SQL Server | Документы Microsoft"
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 99f42ddd8d906799c02b05d856597db7c44a8eb6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-machine-learning-services"></a>Изучение служб машины SQL Server

Обучение машины служб (ранее служб SQL Server 2016 R) SQL Server 2017 г. предоставляет платформу для разработки и развертывания интеллектуальных приложений, предназначенных для получения новых аналитических данных. Поскольку машинное обучение интегрирован с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно analytics близко к данным, избежав затрат и рисков, связанных с перемещением данных.
  
+ В SQL Server 2016 можно легко разрабатывать и развертывать решения на основе популярных языка R для обработки и анализа данных. 

    Возможности включают [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) библиотек, которые обеспечивают новые масштабируемости и производительности решений R и состояние современных алгоритмов в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package).
+ В SQL Server 2017 г можно использовать R и Python для разработки и эксплуатации решений обработки и анализа данных. 

    [Revoscalepy](../python/what-is-revoscalepy.md) библиотека для Python предоставляет контекстах удаленных вычислений и масштабируемость, аналогичные в RevoScaleR.

SQL Server поддерживает повышение производительности, безопасности и управляемости для рабочих нагрузок машин обучения через набор средств и технологий. Можно развернуть R или Python решений с использованием удобный, знакомый методологии SQL и средства. Просто используйте [!INCLUDE[tsql](../../includes/tsql-md.md)] вызов среды выполнения R или Python из ваши рабочие приложения, для построения моделей или получения визуальных элементов. Если вы уже прошли обучение модели, можно создать прогнозы из нее с помощью только T-SQL, в [оценки собственного](../sql-native-scoring.md).

## <a name="machine-learning-in-sql-server-2017"></a>Машинного обучения в SQL Server 2017 г.

+ Установка **службы обучения машины (в базе данных)** во время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программу установки, чтобы обеспечить безопасное выполнение скриптов R или Python на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
    При выборе этого компонента расширения устанавливаются в компоненте database engine для поддержки выполнения кода на языке R или Python. Создается новая служба, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], для управления обменом данными между внешних сред выполнения и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.
  
+ Установка **Microsoft машины обучения Server (изолированный)** на отдельном компьютере, если не нужно использовать в качестве контекста вычислений SQL Server. Сервер обучения машины включает компоненты обучения одного компьютера, а также возможность выполнения задач обучения масштабируемая, распределенная машины веб-службы.
  
+ Установка [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) на удаленных компьютерах для разработки решений, которые могут быть развернуты в SQL Server или серверу обучения компьютера в Windows, Linux или Hadoop.

## <a name="machine-learning-in-sql-server-2016"></a>Машинного обучения в SQL Server 2016

+ Установка **служб R (в базе данных)** во время установки SQL Server 2016, чтобы обеспечить безопасное выполнение скриптов R на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера.
  
    При выборе этого компонента вы получаете возможность запустить сценарий R, с помощью SQL Server в контексте или для выполнения сценария R в хранимой процедуре.
  
+ Установка **Microsoft R Server (изолированный)** из программы установки SQL Server 2016, чтобы установить компоненты R на отдельном компьютере, который можно использовать для разработки и развертывания решений R.

## <a name="how-to-get-started"></a>Начало работы

Программа установки SQL Server предоставляет два варианта:

+ Установка компонентов аналитика в базе данных, т. е интегрирован с SQL Server, или
+ Установите версию автономного машины обучения сервера (или Microsoft R Server), которая поддерживает машинного обучения на масштаб без экземпляра SQL Server.

Если необходимо выполнять код R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо с помощью хранимых процедур или с помощью экземпляра SQL Server в контексте, необходимо установить [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] как описано в [руководство по установке](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md). Этот параметр обеспечивает безопасность максимальный объем данных и интеграции с помощью средств SQL Server.

Microsoft машины обучения Server (изолированный) является отдельным параметром предназначены для использования [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) и [связанные библиотеки Python](../python/what-is-revoscalepy.md) на компьютере Windows, на котором не выполняется SQL Server. Этот параметр требует наличия лицензии Enterprise Edition для SQL Server.
    
Мы рекомендуем установить машины обучения Server (изолированного) на ноутбук или другого удаленного компьютера, для использования в разработке и использовать его для создания и тестирования решения машинного обучения, которые легко могут быть развернуты на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] т.е. под управлением службы обучения машины \(в базе данных\) или другой поддерживаемой контекста вычислений.
  
Можно также использовать **mrsdeploy** пакет, который устанавливается вместе с компьютера сервера обучения для публикации и распространения заданий R и Python веб-службы.

## <a name="additional-resources"></a>Дополнительные ресурсы

+ [Приступая к работе со службами SQL Server машины обучения](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    Описаны типичные сценарии для использования R в SQL Server

+ [Настройка служб SQL Server машины обучения или R службы в базе данных](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    Установить R и связанные базы данных компонентов в рамках программы установки SQL Server
  
+ [Учебники по SQL Server и R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Информация о том, как создавать источники данных SQL Server в коде R и использовать контексты удаленных вычислений. Другие руководства предназначены для разработчиков SQL и демонстрируют, как обучить и развернуть модель R в SQL Server.
